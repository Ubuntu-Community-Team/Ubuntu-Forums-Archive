---
title: "Dual Boot Screen Help"
date: 2008-07-26
forum: General Help
---

### Post by Arbitor on 2008-07-26
Hi, when I boot up my computer, I get to the following boot screen.

Ubuntu 8.04.1, kernal 2.6.24-19-generic
Ubuntu 8.04.1, kernal 2.6.24-19-generic (recovery)
Ubuntu 8.04.1, kernal 2.6.24-16-generic
Ubuntu 8.04.1, kernal 2.6.24-16-generic (recovery)
Ubuntu 8.04.1, memtest86+
Other operating systems:
Windows XP Professional

My question is, how do I remove the ones I don't want? For example, I don't need XP anymore and want it gone from the hard drive. Thanks in advance.

---

### Post by ajmorris on 2008-07-26
> **Arbitor said:**
> Hi, when I boot up my computer, I get to the following boot screen.

Ubuntu 8.04.1, kernal 2.6.24-19-generic
Ubuntu 8.04.1, kernal 2.6.24-19-generic (recovery)
Ubuntu 8.04.1, kernal 2.6.24-16-generic
Ubuntu 8.04.1, kernal 2.6.24-16-generic (recovery)
Ubuntu 8.04.1, memtest86+
Other operating systems:
Windows XP Professional

My question is, how do I remove the ones I don't want? For example, I don't need XP anymore and want it gone from the hard drive. Thanks in advance.

hi there,
to remove entries from grub that you no longer want. Boot up your ubuntu, and open /boot/grub/menu.lst as root. If you scroll down to the bottom of that file, you will see your boot entries. You can remove them here. As for removing windows XP from your hard disk, boot up the ubuntu (or another linux distro) live cd. Open up a partitioning tool, (gparted is most likely what you will want to use) delete your windows XP partition (the partition type of this will be NTFS) then resize your ubuntu partition to take up the free space again if you want ubuntu to use this free space. When you format your XP partition, take extra care that you are indeed deleting your windows partition, and not your ubuntu one, as if you accidentally format the wrong one, it is rather difficult to retrieve your data. Also, it is a good idea to back up any important data before resizing/formatting/deleting partitions.

AJ

---

### Post by Arbitor on 2008-07-26
> **ajmorris said:**
> hi there,
to remove entries from grub that you no longer want. Boot up your ubuntu, and open /boot/grub/menu.lst as root. If you scroll down to the bottom of that file, you will see your boot entries. You can remove them here. As for removing windows XP from your hard disk, boot up the ubuntu (or another linux distro) live cd. Open up a partitioning tool, (gparted is most likely what you will want to use) delete your windows XP partition (the partition type of this will be NTFS) then resize your ubuntu partition to take up the free space again if you want ubuntu to use this free space. When you format your XP partition, take extra care that you are indeed deleting your windows partition, and not your ubuntu one, as if you accidentally format the wrong one, it is rather difficult to retrieve your data. Also, it is a good idea to back up any important data before resizing/formatting/deleting partitions.

AJ

Thanks for the quick reply. I'm a bit of a noob with linux, where do I input the /boot/grub/menu.lst as root? At the boot screen or in the actual ubuntu desktop?

---

### Post by lynlow on 2008-07-27
i find the easiest way to limit the amount of old kernel versions in grub is to get startup manager from synaptic . and for windows you will need to format that partition .

---

### Post by ajmorris on 2008-07-28
> **Arbitor said:**
> Thanks for the quick reply. I'm a bit of a noob with linux, where do I input the /boot/grub/menu.lst as root? At the boot screen or in the actual ubuntu desktop?
 
/boot/grub/menu.lst is file. You need to edit it as root user to change it. Press Alt+F2 and enter gksudo gedit /boot/grub/menu.lst
 
AJ

---

