---
title: "Cannot install grub"
date: 2008-11-04
forum: General Help
---

### Post by Hiperi0n on 2008-11-04
Hi. Yesterday I tried to install ubuntu in one of my friend's computer. However, I puzzled when I reboot after the installation and grub showed an error 17. This seems to happen when there is a bad bios HD configuration, however everything seems fine, I have tried to follow the guides I found for this error but it didn't resolve. I recovered mbr using a super grub disk so he can now boot normally into windows.

My friend has 3 HDs, I have installed ubuntu in the 3rd one, and grub in the first one. Should I try to install grub in the same disc as ubuntu? Would it boot correctly? All 3 disks seem to have the boot flag on, maybe that is the cause of the problem? I am eager to evangelize my friend into ubuntu so I'd appreciate any tips :lolflag:

---

### Post by cdtech on 2008-11-04
You would probably have to set up the GRUB bootloader manually.

You could find the correct device by using the "GRUB" command line:
[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

Examples of the difference from the GNU/Linux and GRUB device names:

1st Physical Hard Drive:
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hda1 ----(hd0,0)----- /dev/sda1-------(hd0,0)
/dev/hda2 ----(hd0,1)----- /dev/sda2-------(hd0,1)
/dev/hda3 ----(hd0,2)----- /dev/sda1-------(hd0,2)
/dev/hda4 ----(hd0,3)------/dev/sda2-------(hd0,3)

2nd Physical Hard Drive:
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hdb1---- (hd1,0)----- /dev/sdb1------ (hd1,0)
/dev/hdb2---- (hd1,1)----- /dev/sdb2------ (hd1,1)
/dev/hdb3---- (hd1,2)----- /dev/sdb1------ (hd1,2)
/dev/hdb4---- (hd1,3)----- /dev/sdb2-------(hd1,3)

Hope this helps ya......

---

### Post by avangardman on 2008-11-04
At first the system search the boot flag. Mark as a boot the partition where is the grub (in your case- first one). A hope it works.

---

### Post by Hiperi0n on 2008-11-04
Yes, I installed grub in the first HD, though it gave me that nasty error 17, so I will try to install it in another HD (the same as ubuntu). If I'm not wrong I will have to mark that HD with the boot flag, and clear from the others.

Edit: Another doubt I have is the following one. I didn't know how many HDs he had so I did a fdisk -l. It showed four, instead of three. However sdb and sdc seemed to be the same disk, in sdc showing the existing partitions. Why is it? Because one type of primary/extended/logical partition looks this way?

---

