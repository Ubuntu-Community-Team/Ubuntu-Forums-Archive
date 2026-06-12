---
title: "USB not recognizable !!"
date: 2009-02-18
forum: Hardware
---

### Post by ryecomp on 2009-02-18
I am using ubuntu 8.10, 

Old USB memory stick normally used in windows not recognizable.
dmesg says sdc or sdc1 device but there is no such device in /dev.

Thanks in advance.

lsusb 
--------
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 006: ID 05e3:0700 Genesys Logic, Inc. SIIG US2256 CompactFlash Card Reader

dmesg 
--------
[86275.688028] usb 4-1: new full speed USB device using uhci_hcd and address 6
[86275.855661] usb 4-1: configuration #1 chosen from 1 choice
[86275.868538] scsi8 : SCSI emulation for USB Mass Storage devices
[86275.870146] usb-storage: device found at 6
[86275.870157] usb-storage: waiting for device to settle before scanning
[86280.869129] usb-storage: device scan complete
[86280.872113] scsi 8:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0.01 PQ: 0 ANSI: 0
[86280.898972] sd 8:0:0:0: [sdc] 500401 512-byte hardware sectors (256 MB)
[86280.905474] sd 8:0:0:0: [sdc] Test WP failed, assume Write Enabled
[86280.905489] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[86280.939103] sd 8:0:0:0: [sdc] 500401 512-byte hardware sectors (256 MB)
[86280.945175] sd 8:0:0:0: [sdc] Test WP failed, assume Write Enabled
[86280.945185] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[86280.945811]  sdc: sdc1
[86280.960234] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[86280.960649] sd 8:0:0:0: Attached scsi generic sg3 type 0
[86461.050003] sd 8:0:0:0: timing out command, waited 180s
[86461.050021] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[86461.050028] sd 8:0:0:0: [sdc] Sense Key : Hardware Error [current] 
[86461.050035] sd 8:0:0:0: [sdc] Add. Sense: Data phase error
[86461.050043] end_request: I/O error, dev sdc, sector 500400
[86461.050049] __ratelimit: 191 callbacks suppressed
[86461.050054] Buffer I/O error on device sdc, logical block 500400
[86641.185932] sd 8:0:0:0: timing out command, waited 180s
[86641.185949] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[86641.185957] sd 8:0:0:0: [sdc] Sense Key : Hardware Error [current] 
[86641.185964] sd 8:0:0:0: [sdc] Add. Sense: Data phase error
[86641.185973] end_request: I/O error, dev sdc, sector 500400
[86641.185980] Buffer I/O error on device sdc, logical block 500400
[86821.237864] sd 8:0:0:0: timing out command, waited 180s
[86821.237883] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[86821.237890] sd 8:0:0:0: [sdc] Sense Key : Hardware Error [current] 
[86821.237897] sd 8:0:0:0: [sdc] Add. Sense: Data phase error
[86821.237905] end_request: I/O error, dev sdc, sector 500400
[86821.237912] Buffer I/O error on device sdc, logical block 500400

---

### Post by taurus on 2009-02-18
What about 

```
sudo fdisk -l
```
I assume it's fat32 filesystem so you could try to mount it to see if that works.

```
sudo mkdir /media/sdc1
sudo mount -t vfat /dev/sdc1 /media/sdc1
df -h
```

---

### Post by ryecomp on 2009-02-19
sudo fdisk -l 

but USB flash not present in the table.
-----

Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02220222

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3580    28756318+  83  Linux
/dev/sda2            3581        3739     1277167+   5  Extended
/dev/sda5            3581        3739     1277136   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08d04302

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

---

### Post by ryecomp on 2009-02-19
When inserted to window2000, it is OK to read/write. 

Any helps ??

---

