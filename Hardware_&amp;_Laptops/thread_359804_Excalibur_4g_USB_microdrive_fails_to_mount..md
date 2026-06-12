---
title: "Excalibur 4g USB microdrive fails to mount."
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by daemonfly on 2007-02-12
*FIXED* Drive ended up failing altogether. Nice how Windows doesn't have an issue writing to bad drives without warning, eh?


Just picked up an Excalibur 4g USB microdrive off Woot, but Ubuntu doesn't want to mount it. Tested it on a Windows box, works fine. Wrote to, and read from just fine, listed as Fat32, etc...   My various regular USB Flash-based drives work just fine in Ubuntu.

Doesn't automount at all.

Testdisk
If I select "Intel/PC partition" it gives me "Partition: read error". If I select "None", it finds a partition:
```
Current partition structure:
     Partition                  Start        End    Size in sectors
   P Unknown                  0   0  1  3905  63 32    7999488
```


For either one, Analyze errors out with the same:
```
Disk /dev/sda - 4095 MB / 3906 MiB - CHS 3906 64 32
Analyse cylinder     6/3905: 00%
Read error at 6/0/1 (lba=12288) (constant read errors all the way through).
```


fsck gives similar errors:
```
fsck -t vfat /dev/sda
fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Read 512 bytes at 0:Input/output error
```


Saved the dmesg spam for last ;)
```
[17282579.520000] usb 2-1.2: new full speed USB device using uhci_hcd and address 16
[17282579.620000] usb 2-1.2: not running at top speed; connect to a high speed hub
[17282579.648000] usb 2-1.2: configuration #1 chosen from 1 choice
[17282579.652000] scsi10 : SCSI emulation for USB Mass Storage devices
[17282579.652000] usb-storage: device found at 16
[17282579.652000] usb-storage: waiting for device to settle before scanning
[17282584.652000] usb-storage: device scan complete
[17282584.656000]   Vendor: CORNICE   Model: Inc. Storage Ele  Rev:  0 0
[17282584.656000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17282584.660000] SCSI device sda: 7999488 512-byte hdwr sectors (4096 MB)
[17282584.664000] sda: Write Protect is off
[17282584.664000] sda: Mode Sense: 03 00 00 00
[17282584.664000] sda: assuming drive cache: write through
[17282584.668000] SCSI device sda: 7999488 512-byte hdwr sectors (4096 MB)
[17282584.672000] sda: Write Protect is off
[17282584.672000] sda: Mode Sense: 03 00 00 00
[17282584.672000] sda: assuming drive cache: write through
[17282584.672000]  sda:<6>sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282585.980000] end_request: I/O error, dev sda, sector 0
[17282585.980000] printk: 9 messages suppressed.
[17282585.980000] Buffer I/O error on device sda, logical block 0
[17282586.060000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282586.060000] end_request: I/O error, dev sda, sector 0
[17282586.060000] Buffer I/O error on device sda, logical block 0
[17282586.060000]  unable to read partition table
[17282586.060000] sd 10:0:0:0: Attached scsi disk sda
[17282586.060000] sd 10:0:0:0: Attached scsi generic sg0 type 0
[17282586.200000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282586.200000] end_request: I/O error, dev sda, sector 7999360
[17282586.200000] Buffer I/O error on device sda, logical block 999920
[17282586.280000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282586.280000] end_request: I/O error, dev sda, sector 7999360
[17282586.280000] Buffer I/O error on device sda, logical block 999920
[17282586.364000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282586.364000] end_request: I/O error, dev sda, sector 7999480
[17282586.364000] Buffer I/O error on device sda, logical block 999935
[17282586.444000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282586.444000] end_request: I/O error, dev sda, sector 7999480
[17282586.444000] Buffer I/O error on device sda, logical block 999935
[17282586.528000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282586.528000] end_request: I/O error, dev sda, sector 7999480
[17282586.528000] Buffer I/O error on device sda, logical block 999935
[17282586.608000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282586.608000] end_request: I/O error, dev sda, sector 7999480
[17282586.608000] Buffer I/O error on device sda, logical block 999935
[17282586.688000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282586.688000] end_request: I/O error, dev sda, sector 7999480
[17282586.688000] Buffer I/O error on device sda, logical block 999935
[17282586.772000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282586.772000] end_request: I/O error, dev sda, sector 7999480
[17282586.772000] Buffer I/O error on device sda, logical block 999935
[17282586.848000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282586.848000] end_request: I/O error, dev sda, sector 7999424
[17282586.932000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282586.932000] end_request: I/O error, dev sda, sector 7999424
[17282587.012000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282587.012000] end_request: I/O error, dev sda, sector 7999472
[17282587.096000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282587.096000] end_request: I/O error, dev sda, sector 7999472
[17282587.176000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282587.176000] end_request: I/O error, dev sda, sector 7999480
[17282587.256000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282587.256000] end_request: I/O error, dev sda, sector 7999480
[17282587.360000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282587.360000] end_request: I/O error, dev sda, sector 0
[17282587.440000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282587.440000] end_request: I/O error, dev sda, sector 0
[17282587.520000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282587.520000] end_request: I/O error, dev sda, sector 0
[17282587.684000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282587.684000] end_request: I/O error, dev sda, sector 0
[17282587.844000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282587.844000] end_request: I/O error, dev sda, sector 8
[17282588.000000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282588.000000] end_request: I/O error, dev sda, sector 16
[17282588.160000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282588.160000] end_request: I/O error, dev sda, sector 24
[17282588.252000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282588.252000] end_request: I/O error, dev sda, sector 32
[17282588.332000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282588.332000] end_request: I/O error, dev sda, sector 0
[17282588.412000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282588.412000] end_request: I/O error, dev sda, sector 0
[17282588.492000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282588.492000] end_request: I/O error, dev sda, sector 0
[17282589.204000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282589.204000] end_request: I/O error, dev sda, sector 40
[17282589.932000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282589.932000] end_request: I/O error, dev sda, sector 48
[17282590.588000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282590.588000] end_request: I/O error, dev sda, sector 56
[17282591.236000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282591.236000] end_request: I/O error, dev sda, sector 64
[17282591.236000] printk: 20 messages suppressed.
[17282591.236000] Buffer I/O error on device sda, logical block 8
[17282591.880000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282591.880000] end_request: I/O error, dev sda, sector 72
[17282592.524000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282592.524000] end_request: I/O error, dev sda, sector 80
[17282593.100000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282593.100000] end_request: I/O error, dev sda, sector 88
[17282593.664000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282593.664000] end_request: I/O error, dev sda, sector 96
[17282594.228000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282594.228000] end_request: I/O error, dev sda, sector 104
[17282594.736000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282594.736000] end_request: I/O error, dev sda, sector 112
[17282595.220000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282595.220000] end_request: I/O error, dev sda, sector 120
[17282595.704000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282595.704000] end_request: I/O error, dev sda, sector 128
[17282596.184000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282596.184000] end_request: I/O error, dev sda, sector 136
[17282596.184000] printk: 8 messages suppressed.
[17282596.184000] Buffer I/O error on device sda, logical block 17
[17282596.600000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282596.600000] end_request: I/O error, dev sda, sector 144
[17282597.004000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282597.004000] end_request: I/O error, dev sda, sector 152
[17282597.404000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282597.404000] end_request: I/O error, dev sda, sector 160
[17282597.764000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282597.764000] end_request: I/O error, dev sda, sector 168
[17282598.088000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282598.088000] end_request: I/O error, dev sda, sector 176
[17282598.408000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282598.408000] end_request: I/O error, dev sda, sector 184
[17282598.728000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282598.728000] end_request: I/O error, dev sda, sector 192
[17282598.980000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282598.980000] end_request: I/O error, dev sda, sector 200
[17282599.220000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282599.220000] end_request: I/O error, dev sda, sector 208
[17282599.460000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282599.460000] end_request: I/O error, dev sda, sector 216
[17282599.672000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282599.672000] end_request: I/O error, dev sda, sector 224
[17282599.832000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282599.832000] end_request: I/O error, dev sda, sector 232
[17282599.988000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282599.988000] end_request: I/O error, dev sda, sector 240
[17282600.148000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282600.148000] end_request: I/O error, dev sda, sector 248
[17282600.240000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282600.240000] end_request: I/O error, dev sda, sector 256
[17282600.324000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282600.324000] end_request: I/O error, dev sda, sector 0
[17282600.404000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282600.404000] end_request: I/O error, dev sda, sector 0
[17282600.484000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282600.484000] end_request: I/O error, dev sda, sector 0
[17282600.564000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282600.564000] end_request: I/O error, dev sda, sector 0
[17282600.648000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282600.648000] end_request: I/O error, dev sda, sector 0
[17282600.728000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282600.728000] end_request: I/O error, dev sda, sector 0
[17282600.808000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282600.808000] end_request: I/O error, dev sda, sector 0
[17282600.892000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282600.892000] end_request: I/O error, dev sda, sector 0
[17282600.972000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282600.972000] end_request: I/O error, dev sda, sector 0
[17282601.052000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.052000] end_request: I/O error, dev sda, sector 0
[17282601.052000] printk: 24 messages suppressed.
[17282601.052000] Buffer I/O error on device sda, logical block 0
[17282601.132000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.132000] end_request: I/O error, dev sda, sector 0
[17282601.216000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.216000] end_request: I/O error, dev sda, sector 0
[17282601.296000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.296000] end_request: I/O error, dev sda, sector 0
[17282601.376000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.376000] end_request: I/O error, dev sda, sector 0
[17282601.456000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.456000] end_request: I/O error, dev sda, sector 0
[17282601.540000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.540000] end_request: I/O error, dev sda, sector 0
[17282601.620000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.620000] end_request: I/O error, dev sda, sector 0
[17282601.700000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.700000] end_request: I/O error, dev sda, sector 0
[17282601.780000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.780000] end_request: I/O error, dev sda, sector 0
[17282601.864000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.864000] end_request: I/O error, dev sda, sector 0
[17282601.956000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282601.956000] end_request: I/O error, dev sda, sector 0
[17282602.100000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282602.100000] end_request: I/O error, dev sda, sector 8
[17282602.244000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282602.244000] end_request: I/O error, dev sda, sector 16
[17282602.336000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282602.336000] end_request: I/O error, dev sda, sector 24
[17282602.416000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282602.416000] end_request: I/O error, dev sda, sector 0
[17282602.496000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282602.496000] end_request: I/O error, dev sda, sector 0
[17282602.740000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282602.740000] end_request: I/O error, dev sda, sector 32
[17282602.980000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282602.980000] end_request: I/O error, dev sda, sector 40
[17282603.220000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282603.220000] end_request: I/O error, dev sda, sector 48
[17282603.392000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282603.392000] end_request: I/O error, dev sda, sector 56
[17282603.552000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282603.552000] end_request: I/O error, dev sda, sector 64
[17282603.708000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282603.708000] end_request: I/O error, dev sda, sector 72
[17282603.856000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282603.856000] end_request: I/O error, dev sda, sector 80
[17282603.932000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282603.932000] end_request: I/O error, dev sda, sector 88
[17282604.008000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282604.008000] end_request: I/O error, dev sda, sector 0
[17282604.092000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282604.092000] end_request: I/O error, dev sda, sector 0
[17282604.172000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282604.172000] end_request: I/O error, dev sda, sector 0
[17282604.252000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282604.252000] end_request: I/O error, dev sda, sector 0
[17282604.820000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282604.820000] end_request: I/O error, dev sda, sector 96
[17282605.384000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282605.384000] end_request: I/O error, dev sda, sector 104
[17282605.932000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282605.932000] end_request: I/O error, dev sda, sector 112
[17282606.416000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282606.416000] end_request: I/O error, dev sda, sector 120
[17282606.416000] printk: 31 messages suppressed.
[17282606.416000] Buffer I/O error on device sda, logical block 15
[17282606.900000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282606.900000] end_request: I/O error, dev sda, sector 128
[17282607.380000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282607.380000] end_request: I/O error, dev sda, sector 136
[17282607.796000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282607.796000] end_request: I/O error, dev sda, sector 144
[17282608.196000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282608.196000] end_request: I/O error, dev sda, sector 152
[17282608.600000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282608.600000] end_request: I/O error, dev sda, sector 160
[17282608.948000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282608.948000] end_request: I/O error, dev sda, sector 168
[17282609.268000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282609.268000] end_request: I/O error, dev sda, sector 176
[17282609.588000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282609.588000] end_request: I/O error, dev sda, sector 184
[17282609.908000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282609.908000] end_request: I/O error, dev sda, sector 192
[17282610.164000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282610.164000] end_request: I/O error, dev sda, sector 200
[17282610.400000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282610.400000] end_request: I/O error, dev sda, sector 208
[17282610.640000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282610.640000] end_request: I/O error, dev sda, sector 216
[17282610.868000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282610.868000] end_request: I/O error, dev sda, sector 224
[17282611.028000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282611.028000] end_request: I/O error, dev sda, sector 232
[17282611.028000] printk: 13 messages suppressed.
[17282611.028000] Buffer I/O error on device sda, logical block 29
[17282611.184000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282611.184000] end_request: I/O error, dev sda, sector 240
[17282611.344000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282611.344000] end_request: I/O error, dev sda, sector 248
[17282611.436000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282611.436000] end_request: I/O error, dev sda, sector 256
[17282611.520000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282611.520000] end_request: I/O error, dev sda, sector 0
[17282611.600000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282611.600000] end_request: I/O error, dev sda, sector 0
[17282611.680000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282611.680000] end_request: I/O error, dev sda, sector 0
[17282611.760000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282611.760000] end_request: I/O error, dev sda, sector 0
[17282611.840000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282611.840000] end_request: I/O error, dev sda, sector 0
[17282611.924000] sd 10:0:0:0: SCSI error: return code = 0x10070000
[17282611.924000] end_request: I/O error, dev sda, sector 0
```

---

### Post by Crochetchick on 2007-02-17
I just bought the same usb drive from woot, also. Is it possible to automount at all? I don't know how to make it work. Can you tell me how you made it work? I don't know how to mount the drive, or understand what that is exactly. When I ordered it, I just assumed it would plug in and pop up like other flash drives. What should I do?

Update: I miss read your post and saw the word fixed and assumed you got it working. Then on top it said fixed and drive not working. Sorry to ask something you can't answer.

---

### Post by Crochetchick on 2007-03-14
I am still feeling my way through Linux, and really don't know how to do alot of things.

Here is what I did so far on my own to try making this flash drive mount.

First thing I did was look up on the Ubuntu wiki and found instructions how to  mount a hard drive.
Here: [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

Following the steps provided:
1. Determine Drive Information
------------------------------

We assume that the hard drive is physically installed and detected by the BIOS.

To determine the path that your system has assigned to the new hard drive, open a terminal and run:
-------------------
-sudo lshw -C disk-
-------------------

My results:
 *-disk
       description: SCSI Disk
       product: Inc. Storage Ele
       vendor: CORNICE
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 00
       size: 3906MB

Be sure to note the "logical name." We'll be using this later.

2. Formating
Cannot format the drive:

Command Used:
-----------------------
--sudo fdisk /dev/sda--
-----------------------
error: Unable to read /dev/sda
 
When going through gparted:
     1. shows drive unallocated
     2. When clicking new for partition, 
        Popup asking to set Disklabel on /dev/sda
        By default GParted creates an msdos disklabel
     3. When clicking create, error: Error while setting new disklabel

These are the only choices available.

3. Create a Mount Point
-----------------------

Now that the drive is partitioned and formatted, you need to choose a mount point. This will be the location from which you will access the drive in the future. I would recommend using a mount point with "/media." For this example, we'll use the path "/media/mynewdrive"

My command:
----------------------------------
--sudo mkdir /media/excaliburUSB--
----------------------------------

Now we can mount the drive to the mount point.

My command:
-------------------------------------------
--sudo mount /dev/sda /media/excaliburUSB--
-------------------------------------------
My error after command:
mount: you must specify the filesystem type


That is what I did so far. I don't know how to check the device for errors as daemonfly has stated in his post. Does anyone have some advise on this?

---

