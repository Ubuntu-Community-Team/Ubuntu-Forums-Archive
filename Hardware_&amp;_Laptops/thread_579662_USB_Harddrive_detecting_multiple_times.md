---
title: "USB Harddrive detecting multiple times"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by doobiest on 2007-10-18
Hey there,

This is the best category I could find to post this. Also I couldnt find anything relevant to my question.

The issue is simple to describe.

1. Plug USB HDD into laptop
2. Device detects 8 times
3. Ubuntu assigned 8 device designations to the one device (sdb,sdc,sdd,sde,sdf,sdg,sdh,sdg)
4. Due to this Ubuntu also mounts the same drive 8 times (/media/drive1, /media/drive2, etc.)

So basically whats up here is I plug one usb hdd in, it gets assigned 8 devices under /dev/, it gets mounted 8 times.

Here's dmesg: (sorry about the white space, copied from outlook)


```
[89688.226666] scsi9 : SCSI emulation for USB Mass Storage devices

[89688.227988] usb-storage: device found at 5

[89688.227993] usb-storage: waiting for device to settle before scanning

[89693.214708] usb-storage: device scan complete

[89693.286494] usb 5-2.3: reset high speed USB device using ehci_hcd and address 5

[89694.612838] scsi 9:0:0:0: Direct-Access     Initio   WD1600BEVS-22RST 3.01 PQ: 0 ANSI: 0

[89694.613558] scsi 9:0:0:1: Direct-Access     Initio   WD1600BEVS-22RST 3.01 PQ: 0 ANSI: 0

[89694.614308] scsi 9:0:0:2: Direct-Access     Initio   WD1600BEVS-22RST 3.01 PQ: 0 ANSI: 0

[89694.615052] scsi 9:0:0:3: Direct-Access     Initio   WD1600BEVS-22RST 3.01 PQ: 0 ANSI: 0

[89694.615951] scsi 9:0:0:4: Direct-Access     Initio   WD1600BEVS-22RST 3.01 PQ: 0 ANSI: 0

[89694.616956] scsi 9:0:0:5: Direct-Access     Initio   WD1600BEVS-22RST 3.01 PQ: 0 ANSI: 0

[89694.618008] scsi 9:0:0:6: Direct-Access     Initio   WD1600BEVS-22RST 3.01 PQ: 0 ANSI: 0

[89694.619224] scsi 9:0:0:7: Direct-Access     Initio   WD1600BEVS-22RST 3.01 PQ: 0 ANSI: 0

[89694.620655] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)

[89694.621398] sdb: Write Protect is off

[89694.621402] sdb: Mode Sense: 00 00 00 00

[89694.621405] sdb: assuming drive cache: write through

[89694.622268] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)

[89694.622893] sdb: Write Protect is off

[89694.622897] sdb: Mode Sense: 00 00 00 00

[89694.622899] sdb: assuming drive cache: write through

[89694.622903]  sdb: sdb1

[89694.673129] sd 9:0:0:0: Attached scsi disk sdb

[89694.673183] sd 9:0:0:0: Attached scsi generic sg2 type 0

[89694.675509] SCSI device sdc: 312581808 512-byte hdwr sectors (160042 MB)

[89694.676256] sdc: Write Protect is off

[89694.676259] sdc: Mode Sense: 00 00 00 00

[89694.676262] sdc: assuming drive cache: write through

[89694.677250] SCSI device sdc: 312581808 512-byte hdwr sectors (160042 MB)

[89694.677875] sdc: Write Protect is off

[89694.677878] sdc: Mode Sense: 00 00 00 00

[89694.677880] sdc: assuming drive cache: write through

[89694.677885]  sdc: sdc1

[89694.678450] sd 9:0:0:1: Attached scsi disk sdc

[89694.678503] sd 9:0:0:1: Attached scsi generic sg3 type 0

[89694.679478] SCSI device sdd: 312581808 512-byte hdwr sectors (160042 MB)

[89694.680256] sdd: Write Protect is off

[89694.680260] sdd: Mode Sense: 00 00 00 00

[89694.680262] sdd: assuming drive cache: write through

[89694.681536] SCSI device sdd: 312581808 512-byte hdwr sectors (160042 MB)

[89694.682368] sdd: Write Protect is off

[89694.682373] sdd: Mode Sense: 00 00 00 00

[89694.682375] sdd: assuming drive cache: write through

[89694.682383]  sdd: sdd1

[89694.683176] sd 9:0:0:2: Attached scsi disk sdd

[89694.683229] sd 9:0:0:2: Attached scsi generic sg4 type 0

[89694.686469] SCSI device sde: 312581808 512-byte hdwr sectors (160042 MB)

[89694.687229] sde: Write Protect is off

[89694.687233] sde: Mode Sense: 00 00 00 00

[89694.687235] sde: assuming drive cache: write through

[89694.688222] SCSI device sde: 312581808 512-byte hdwr sectors (160042 MB)

[89694.688846] sde: Write Protect is off

[89694.688850] sde: Mode Sense: 00 00 00 00

[89694.688852] sde: assuming drive cache: write through

[89694.688858]  sde: sde1

[89694.689419] sd 9:0:0:3: Attached scsi disk sde

[89694.689471] sd 9:0:0:3: Attached scsi generic sg5 type 0

[89694.692737] SCSI device sdf: 312581808 512-byte hdwr sectors (160042 MB)

[89694.693461] sdf: Write Protect is off

[89694.693464] sdf: Mode Sense: 00 00 00 00

[89694.693467] sdf: assuming drive cache: write through

[89694.694331] SCSI device sdf: 312581808 512-byte hdwr sectors (160042 MB)

[89694.694956] sdf: Write Protect is off

[89694.694960] sdf: Mode Sense: 00 00 00 00

[89694.694961] sdf: assuming drive cache: write through

[89694.694968]  sdf: sdf1

[89694.696560] sd 9:0:0:4: Attached scsi disk sdf

[89694.696615] sd 9:0:0:4: Attached scsi generic sg6 type 0

[89694.699094] SCSI device sdg: 312581808 512-byte hdwr sectors (160042 MB)

[89694.699949] sdg: Write Protect is off

[89694.699954] sdg: Mode Sense: 00 00 00 00

[89694.699956] sdg: assuming drive cache: write through

[89694.700802] SCSI device sdg: 312581808 512-byte hdwr sectors (160042 MB)

[89694.701440] sdg: Write Protect is off

[89694.701444] sdg: Mode Sense: 00 00 00 00

[89694.701446] sdg: assuming drive cache: write through

[89694.701454]  sdg: sdg1

[89694.702012] sd 9:0:0:5: Attached scsi disk sdg

[89694.702068] sd 9:0:0:5: Attached scsi generic sg7 type 0

[89694.703578] SCSI device sdh: 312581808 512-byte hdwr sectors (160042 MB)

[89694.704310] sdh: Write Protect is off

[89694.704314] sdh: Mode Sense: 00 00 00 00

[89694.704317] sdh: assuming drive cache: write through

[89694.705177] SCSI device sdh: 312581808 512-byte hdwr sectors (160042 MB)

[89694.705928] sdh: Write Protect is off

[89694.705932] sdh: Mode Sense: 00 00 00 00

[89694.705934] sdh: assuming drive cache: write through

[89694.705944]  sdh: sdh1

[89694.706864] sd 9:0:0:6: Attached scsi disk sdh

[89694.706917] sd 9:0:0:6: Attached scsi generic sg8 type 0

[89694.708831] SCSI device sdi: 312581808 512-byte hdwr sectors (160042 MB)

[89694.709544] sdi: Write Protect is off

[89694.709548] sdi: Mode Sense: 00 00 00 00

[89694.709550] sdi: assuming drive cache: write through

[89694.710539] SCSI device sdi: 312581808 512-byte hdwr sectors (160042 MB)

[89694.711295] sdi: Write Protect is off

[89694.711300] sdi: Mode Sense: 00 00 00 00

[89694.711302] sdi: assuming drive cache: write through

[89694.711310]  sdi: sdi1

[89694.712642] sd 9:0:0:7: Attached scsi disk sdi

[89694.712695] sd 9:0:0:7: Attached scsi generic sg9 type 0

[89697.935462] NTFS-fs warning (device sde1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.

[89698.021823] NTFS volume version 3.1.

[89698.134615] NTFS-fs warning (device sdh1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.

[89698.189137] NTFS volume version 3.1.

[89698.312355] NTFS-fs warning (device sdc1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.

[89698.359819] NTFS volume version 3.1.

[89698.554454] NTFS-fs warning (device sdd1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.

[89698.602315] NTFS volume version 3.1.

[89698.696013] NTFS-fs warning (device sdf1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.

[89698.742839] NTFS volume version 3.1.

[89698.828890] NTFS-fs warning (device sdb1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.

[89698.872610] NTFS volume version 3.1.

[89698.948583] NTFS-fs warning (device sdi1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.

[89698.987812] NTFS volume version 3.1.

[89699.067709] NTFS-fs warning (device sdg1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.

[89699.108499] NTFS volume version 3.1.

```

Any thoughts?

---

