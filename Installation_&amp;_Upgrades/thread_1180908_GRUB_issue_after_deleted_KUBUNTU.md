---
title: "GRUB issue after deleted KUBUNTU"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by ganeshkumarb on 2009-06-07
Hi,
I have installed Kubuntu and faced package update problems. So thought of going to Ubuntu so to delete Kubuntu. I deleted the allocated drives from Windows XP as mentioned in one of the Forum. After i restarted my machine i am unable to login to XP. I think i might had Linux as my primary bootup OS.
 
I am keep on getting 
GRUB Loading stage1.5 
 
GRUB loading. please wait...
Error 22.
 
Even i tried to install ubuntu but i could not.
So please help me on this. I am new to Installations...

---

### Post by confused57 on 2009-06-07
Please boot your Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```

If you're using Kubuntu, open a konsole & enter the above.

Here's a thread for reinstalling Window's IPL to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)
instructions from the thread:
```
sudo apt-get install ms-sys
ms-sys --mbr /dev/sda
```

"sudo fdisk -l" will show your hard drive(s) partitions, if you only have one hard drive, it should be designated as /dev/sda.

What problems are you having when you try to install Ubuntu?

---

