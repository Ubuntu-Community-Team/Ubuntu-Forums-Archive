---
title: "GRUB reinstallation problems"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by eZtaR on 2007-07-16
Okay so i had to install windows xp to do some gaming, windows overwrote my mbr as expected, but now i'm home and i want grub to return and windows to disappear.

So i did this:
[list]
[*] Booted the live cd, which recognized my partitiontable and read the files of my linux-partition just fine.
[*] Opened a terminal and did the following
[*] sudo grub
[*] find /dev/grub/stage1
[*] root (hd0,1)
[*] setup (hd0,1)
[*] quit
[*] reboot
[/list]


So now i have a grub menu which contains my two linux kernels but when i press any one of them i get **Error 17: Cannot mount partition**

How do i fix this?

---

### Post by merlinus on 2007-07-16
SuperGrub to the rescue:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by eZtaR on 2007-07-16
nvm i did as described in [this topic](http://ubuntuforums.org/showthread.php?t=351884) and it worked :)

---

