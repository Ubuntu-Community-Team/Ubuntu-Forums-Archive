---
title: "Brother Printer Scanning Problem"
date: 2008-12-01
forum: Hardware
---

### Post by DarkGhostFA on 2008-12-01
I have a brother mfc-9700 and i was trying to find a way to scan multiple pages at once using the scan key and saving directly to pdf. I have changed my scan script to not open any program and just save directly to pdf. Additionally is it possible to force the paper size of the scan, because the printer seems to be set to legal size instead of the standard letter.

```
#! /bin/sh
set +o noclobber
#
#   $1 = scanner device
#   $2 = friendly name
#

#   
#       100,200,300,400,600
#
resolution=100
device=$1
mkdir -p ~/brscan
if [ "`which usleep`" != '' ];then
    usleep 10000
else
    sleep  0.01
fi
output_file=`mktemp ~/pdfscan/scan.XXXXXX`
echo "scan from $2($device) to $output_file"
scanimage --device-name "$device" --resolution $resolution \
| pnmtops | gs -q -dNOPAUSE -sDEVICE=pdfwrite \
-sOutputFile=- - > "$output_file".pdf
rm -f $output_file
```

---

