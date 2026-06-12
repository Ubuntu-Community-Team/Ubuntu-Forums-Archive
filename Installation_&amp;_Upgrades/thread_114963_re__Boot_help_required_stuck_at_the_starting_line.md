---
title: "re  Boot help required stuck at the starting line"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by donaldd on 2006-01-09
Hello everyone appreciate if someone can show me the way to resolve a problem I'm experiencing.

Running a couple of xp instances each from there own partition on my laptop, do not want to mess with MBR.

I created 3 more partitions 
/  ext3
/home ext3
/swap 
then installed UBUNTU, tried to configure Grub and Lilo on a bootable dos fat32 usb stick(my preference) and fat32 floppy using the install process, frustratingly cannot boot into Ubuntu.  I'm not sure if I should format the usb drive as fat16,fat32,ext2 or ext3, do I need create /boot on it,  edit any files? The usb drive mounts as /dev/sdb.

Thanks in advance.

---

### Post by donaldd on 2006-01-10
Almost there, used install process to format usb stick fat16, mount point /dos, installed lilo to it /dev/sdb, unfortunately rebooted into usb a: prompt. Managed to boot into Ubuntu by using the live cdrom which mounted usb enabling access to linux partition. Please could someone tell me how to add needed files to usb.

---

