---
title: "Problem with USB"
date: 2013-01-22
forum: Hardware
---

### Post by jamh on 2013-01-22
Hello all,

My daughter (who has only known ubuntu all her life :) recently upgraded to "Precise" and noticed that her USB ports are not working.  I looked into this a bit and couldn't figure out what was going on, so I'm turning to you guys to help me fix this for her.

Here's the output of dmesg after plugging in an ipod, for example:

[  719.600052] usb 1-6: new high-speed USB device number 8 using ehci_hcd
[  719.672315] hub 1-0:1.0: unable to enumerate USB device on port 6
[  733.072060] usb 1-1: new high-speed USB device number 9 using ehci_hcd
[  733.213148] usb-storage 1-1:1.0: Quirks match for vid 05ac pid 120a: 10
[  733.213198] scsi7 : usb-storage 1-1:1.0
[  734.213429] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  734.220356] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  734.222007] sd 7:0:0:0: [sdb] Adjusting the sector count from its reported value: 7999488
[  734.222021] sd 7:0:0:0: [sdb] 7999487 512-byte logical blocks: (4.09 GB/3.81 GiB)
[  734.223252] sd 7:0:0:0: [sdb] Write Protect is off
[  734.223260] sd 7:0:0:0: [sdb] Mode Sense: 68 00 00 08
[  734.225007] sd 7:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  734.227631] sd 7:0:0:0: [sdb] Adjusting the sector count from its reported value: 7999488
[  734.234847]  sdb: sdb1 sdb2
[  734.236873] sd 7:0:0:0: [sdb] Adjusting the sector count from its reported value: 7999488
[  734.239747] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  734.407561] usb 1-1: USB disconnect, device number 9


So I don't understand why it got disconnected right away.  Also lsusb doesn't show it:

sema@tulle:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)

---

### Post by jamh on 2013-01-22
fdisk doesn't show anything (not after the disconnect):

 sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c4f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    68360191    34179072   83  Linux
/dev/sda2        68362238    78125055     4881409    5  Extended
/dev/sda5        68362240    78125055     4881408   82  Linux swap / Solaris

---

### Post by jamh on 2013-01-22
After diabling ehci:

[ 1849.596057] usb 2-1: new full-speed USB device number 7 using uhci_hcd
[ 1849.784503] usb-storage 2-1:1.0: Quirks match for vid 05ac pid 120a: 10
[ 1849.784555] scsi11 : usb-storage 2-1:1.0
[ 1850.789128] scsi 11:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1850.796318] sd 11:0:0:0: Attached scsi generic sg2 type 0
[ 1850.800253] sd 11:0:0:0: [sdb] Adjusting the sector count from its reported value: 7999488
[ 1850.800267] sd 11:0:0:0: [sdb] 7999487 512-byte logical blocks: (4.09 GB/3.81 GiB)
[ 1850.805338] sd 11:0:0:0: [sdb] Write Protect is off
[ 1850.805347] sd 11:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 1850.810098] sd 11:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1850.819095] sd 11:0:0:0: [sdb] Adjusting the sector count from its reported value: 7999488
[ 1850.843316]  sdb: sdb1 sdb2
[ 1850.852113] sd 11:0:0:0: [sdb] Adjusting the sector count from its reported value: 7999488
[ 1850.866110] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 1850.948114] usb 2-1: USB disconnect, device number 7
[ 1850.952264] scsi 11:0:0:0: rejecting I/O to offline device
[ 1850.952275] scsi 11:0:0:0: [sdb] killing request
[ 1850.952298] scsi 11:0:0:0: [sdb] Unhandled error code
[ 1850.952303] scsi 11:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1850.952312] scsi 11:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1850.952332] end_request: I/O error, dev sdb, sector 0
[ 1850.952338] quiet_error: 486 callbacks suppressed
[ 1850.952344] Buffer I/O error on device sdb, logical block 0
[ 1850.952351] Buffer I/O error on device sdb, logical block 1
[ 1850.952356] Buffer I/O error on device sdb, logical block 2
[ 1850.952361] Buffer I/O error on device sdb, logical block 3
[ 1850.952366] Buffer I/O error on device sdb, logical block 4
[ 1850.952371] Buffer I/O error on device sdb, logical block 5
[ 1850.952376] Buffer I/O error on device sdb, logical block 6
[ 1850.952382] Buffer I/O error on device sdb, logical block 7
[ 1850.953776] Buffer I/O error on device sdb, logical block 0
[ 1850.953785] Buffer I/O error on device sdb, logical block 1

---

