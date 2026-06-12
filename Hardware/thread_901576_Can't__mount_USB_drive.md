---
title: "Can't  mount USB drive"
date: 2008-08-26
forum: Hardware
---

### Post by bobbert68 on 2008-08-26
I have Xubuntu 8.04 newly installed on my laptop.  When I plug in my USB HDD, I get the error:

> mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so.

dmesg says:

> [  853.939418] usb 5-1: new high speed USB device using ehci_hcd and address 14
[  854.078114] usb 5-1: configuration #1 chosen from 1 choice
[  854.099993] scsi6 : SCSI emulation for USB Mass Storage devices
[  854.110612] usb-storage: device found at 14
[  854.110631] usb-storage: waiting for device to settle before scanning
[  857.905175] usb-storage: device scan complete
[  857.906938] scsi 6:0:0:0: Direct-Access     ATP      ToughDrive       1100 PQ: 0 ANSI: 0 CCS
[  857.911614] sd 6:0:0:0: [sdc] 13470270 512-byte hardware sectors (6897 MB)
[  857.923046] sd 6:0:0:0: [sdc] Write Protect is off
[  857.923074] sd 6:0:0:0: [sdc] Mode Sense: 43 00 00 00
[  857.923087] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  857.928199] sd 6:0:0:0: [sdc] 13470270 512-byte hardware sectors (6897 MB)
[  857.930083] sd 6:0:0:0: [sdc] Write Protect is off
[  857.930107] sd 6:0:0:0: [sdc] Mode Sense: 43 00 00 00
[  857.930119] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  857.930149]  sdc: sdc1 sdc2
[  857.977785] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[  857.977970] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  859.324054] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[  859.805041] UDF-fs: No VRS found
[  859.869345] ISOFS: Unable to identify CD-ROM format.


I'm very new and I have no idea where to start.  Any help would be greatly appreciated.

---

### Post by Crafty Kisses on 2008-08-26
Have you tried manually mounting it?

---

### Post by az on 2008-08-26
What is supposed to be on that hard drive?

Because it seems to be unformatted.  If there is supposed to be a filesystem there, you can try to recover it.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://ubuntu-rescue-remix.org/node/57](http://ubuntu-rescue-remix.org/node/57)

---

### Post by bobbert68 on 2008-08-26
I was able to mount the drive manually, but was unable to unmount it.  I was first given an error that the drive was not listed in fstab.  When I tried to manually unmount it, I was told that the unmount command was not found.  So then I just unplugged it and reinsterted it and it seems to automount fine now... interesting.

Any idea about why I can't manually unmount it?

---

### Post by az on 2008-08-26
> **bobbert68 said:**
> I was told that the unmount command was not found.  So t

If you are certain that you typed it properly, you may have hardware problems.  Faulty ram or CPU overheating may cause errors like this.

[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by bobbert68 on 2008-09-01
Update:

The problem was only fixed for that session and reappeared after restart.

When I originally installed Xubuntu, I used a USB HDD.  I reinstalled it using an external drive and now I have no problems with mounting drives.

---

