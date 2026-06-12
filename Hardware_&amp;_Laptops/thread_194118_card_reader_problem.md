---
title: "card reader problem"
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by kanagawa on 2006-06-11
Hello, I am running stock xubuntu 6.06 on a Sharp pc-cv50 laptop.

It has a built-in SD-card and CF-card reader. 

The SD-card reader never worked under Linux, but Dapper can use it -- almost...

After booting the computer, if I have an SD card in the reader, then it will find it: fdisk -l will list it under /dev/mmc0blk0p1 and everything is happy.

But if I remove the card from the reader and then put it back, there is a good chance that the /dev/mmcblk0p1 device will not reappear. 

It's like the daemon or subsystem responsible for recognising the dev is gone. 

Any ideas, how can I fix it?

---

### Post by arkTIK on 2006-06-14
I'm running XUBUNTU on a Toshiba Satellite M50 with integrated card reader. The reader works every time I insert / remove a card. fdisk shows the entry every time mounted or not mounted.
The only thing I did was to add below entry to /etc/fstab
/dev/mmcblk0p1 /media/sdcard auto noauto,rw,user,exec,sync   0 0

Maybe lshw [list hardware] or hal-device-manager might be helpful to troubleshoot the card reader.

Good luck

---

