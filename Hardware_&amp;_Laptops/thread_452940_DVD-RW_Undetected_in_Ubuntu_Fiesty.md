---
title: "DVD-RW Undetected in Ubuntu Fiesty"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by dirkduck on 2007-05-23
I installed Ubuntu a couple weeks ago on a dual boot setup with Windows XP.  Since then, I have tried playing DVD's in my DVD-RW drive in both Ubuntu and Windows, but neither have read anything in the drive (nor have plain data CD's worked).  Windows' device manager still says that there is a CD/DVD drive installed (actually a double copy...not sure why, but it's Windows...).  My fstab file includes the line: 
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```  

I just installed "hotswap," but "hotswap -cdrom" states that there is no IDE device installed.  Could anyone help?  Thanks.

---

### Post by Rescue9 on 2007-05-24
hotswap is designed to work with ide, not pata. This is the problem. Search the message boards... lots of lappy users are having problems since the upgrade to feisty.

---

