---
title: "Card reader samsung sf310 not working"
date: 2011-06-27
forum: Hardware
---

### Post by josvanr on 2011-06-27
it used to work fine, but now...: the sd card reader.. 
I tried an external usb card reader, that still works
fine. (kubuntu 11.04)

If I stick my sd card in the built-in card reader, 
nothing happens. I tried to mount manually:

root@samsungsucks:~# mount -t vfat /dev/sdb /x
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

though I'm not shure if sdb is the right device.

dmesg output see below...

josvanr





[ 1459.424881] usb 2-1.3: device descriptor read/8, error -110
[ 1464.536371] usb 2-1.3: device descriptor read/8, error -110
[ 1464.712096] usb 2-1.3: new full speed USB device using ehci_hcd and address 21
[ 1469.723737] usb 2-1.3: device descriptor read/8, error -110
[ 1474.835357] usb 2-1.3: device descriptor read/8, error -110
[ 1474.939169] hub 2-1:1.0: unable to enumerate USB device on port 3
[ 1475.138851] usb 2-1.4: new high speed USB device using ehci_hcd and address 22
[ 1475.236784] scsi8 : usb-storage 2-1.4:1.0
[ 1476.234741] scsi 8:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0207 PQ: 0 ANSI: 0
[ 1476.236332] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 1476.370672] sd 8:0:0:0: [sdb] 15523840 512-byte logical blocks: (7.94 GB/7.40 GiB)
[ 1476.371908] sd 8:0:0:0: [sdb] Write Protect is off
[ 1476.371914] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1476.372924] sd 8:0:0:0: [sdb] No Caching mode page present
[ 1476.372931] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1476.376899] sd 8:0:0:0: [sdb] No Caching mode page present
[ 1476.376906] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1476.387887]  sdb: sdb1
[ 1476.391219] sd 8:0:0:0: [sdb] No Caching mode page present
[ 1476.391226] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1476.391232] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 1612.918351] usb 2-1.4: USB disconnect, address 22
[ 1617.405771] usb 2-1.3: new full speed USB device using ehci_hcd and address 23
[ 1632.452711] usb 2-1.3: device descriptor read/64, error -110
[ 1647.603474] usb 2-1.3: device descriptor read/64, error -110
[ 1647.779178] usb 2-1.3: new full speed USB device using ehci_hcd and address 24

---

