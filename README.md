# VCF Operations Report Runner

Runs a report in VCF Operations and writes the result to a file or standard out. This is useful for exporting 
data from VCF Operations using the command line or scheduled jobs.

The command takes a report name and the resource kind and name of a top level resource (e.g. a Datacenter) and run
a report with that resource as a parent object (e.g. processes all clusters under Datacenter)

## Usage

```
python generate_report.py [-h] -H HOST -u USER -p PASSWORD [-a AUTHSOURCE] [-k ADAPTERKIND] -r RESOURCEKIND -n RESOURCENAME -R REPORTNAME [-o OUTPUTFILE] [-U]
```

### Arguments
```
  -h, --help                                        Show this help message and exit
  -H HOST, --host HOST                              VCF Operations FQDN or IP
  -u USER, --user USER                              VCF Operation user
  -p PASSWORD, --password PASSWORD                  VCF Operations password
  -a AUTHSOURCE, --authsource AUTHSOURCE            VCF Operations Authentication source (default is internal) 
  -k ADAPTERKIND, --adapterkind ADAPTERKIND         Top level resource Adapter Kind (default is VMWARE)
  -r RESOURCEKIND, --resourcekind RESOURCEKIND      Top level resource kind
  -n RESOURCENAME, --resourcename RESOURCENAME      Top level resource name
  -R REPORTNAME --reportname REPORTNAME             Name ofd report to run
  -o OUTPUTFILE --output OUTPUTFILE                 Output file (default is stdout)
  -U --unsafe                                       Skip SSL verification (not recommended in production)
 
```

## Example 
```commandline
python generate_report.py -H vrops.example.com -u admin -p secret -r VirtualMachine -R "My Report" 
```

## Sample output
```text
﻿"Name","Disk Space|Total Capacity","Storage|Total IOPS","Memory|Heap","Memory|Consumed","CPU|Demand (%)"
"vcf-cl01","68.1 TB","5,053.5","0 KB","2.5 TB","27.88"
"mgmt-cluster01","60.34 TB","5,866.6","0 KB","899.42 GB","24.43"
```
