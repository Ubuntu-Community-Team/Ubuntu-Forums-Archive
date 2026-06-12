---
title: "External Hard Drive Mounted as CD"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by jacc1234 on 2007-06-11
EDIT: I AM GOING TO RETURN THIS DRIVE FOR A WD. NOTE TO ALL LINUX USERS: STAY AWAY FROM ACOMODATA EXTERNAL DRIVES!!!

I just go a 500gb external had drive and when I plug it in it is mounted as a cd drive at /mount/cd part. I am not sure how to change this so any help would be great. Here also is a copy of my message log:

Jun 11 16:41:27 ubuntudesktop kernel: [82105.367747] usb 2-6: new high speed USB device using ehci_hcd and address 7
Jun 11 16:41:28 ubuntudesktop kernel: [82105.434155] usb 2-6: configuration #1 chosen from 1 choice
Jun 11 16:41:28 ubuntudesktop kernel: [82105.434340] scsi5 : SCSI emulation for USB Mass Storage devices
Jun 11 16:41:33 ubuntudesktop kernel: [82107.915274] scsi 5:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
Jun 11 16:41:33 ubuntudesktop kernel: [82107.916699] scsi 5:0:0:1: Direct-Access     DMI      USB2.0 Storage   1.15 PQ: 0 ANSI: 0
Jun 11 16:41:33 ubuntudesktop kernel: [82107.936031] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
Jun 11 16:41:33 ubuntudesktop kernel: [82107.936120] sr 5:0:0:0: Attached scsi generic sg2 type 5
Jun 11 16:41:33 ubuntudesktop kernel: [82107.938125] sd 5:0:0:1: Attached scsi disk sdb
Jun 11 16:41:33 ubuntudesktop kernel: [82107.938162] sd 5:0:0:1: Attached scsi generic sg3 type 0

It is an acomodata hard drive and has a "cd partition" which is the only one being detected.

Your HybridDrive uses an advanced partition scheme called VirtualCD + SecureHD. The Drive was formatted at the factory with two partitions. As the name implies, one is the CD partition; the other is the HD (Hard Disk) partition. When you connect the Drive to your computer, the two partitions will mount as separate, distinct volumes, as if they were two discrete devices.

I found another post with the same issue but the only solution i found was to plug it into a windows machine which i dont have.


Thanks,
jacc1234

---

