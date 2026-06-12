---
title: "XP Partition not mounting and can not boot"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by austin286 on 2008-03-06
I installed Ubuntu 7.10 and dual booted with XP MCE. Well, windows got rid of the GRUB bootloader causing me to not boot ubuntu. well, i re-installed grub and now XP MCE will not boot. it comes up in the boot menu, but will not boot. Ubuntu treats the XP partition as an unmounted drive and it will not mount it. i get an error that states:
"Unexpected clusters per mft record (-1). Failed to mount '/devsda1': Invalid argument The device '/dev/sda1" doesn't have a valid NTFS. Maybe you selected the wrong device? Or the whole disk instead of a partition (e.g. /dev/hda, not /dev/hda1)?"
Please help. Im still new to linux but have a large knowledge of computers, and i still need files the are on the XP partition. Thanks!

---

### Post by logos34 on 2008-03-06
If you have an XP install CD, boot from it into the recovery console and run

**chkdsk /r**

---

### Post by austin286 on 2008-03-06
that was my first guess, so i did and it went straight to the windows partition editor, not anywhere i can select repair. i might try a different disk.

---

