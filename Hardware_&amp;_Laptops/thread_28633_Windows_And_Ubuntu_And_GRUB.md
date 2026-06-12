---
title: "Windows And Ubuntu And GRUB"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by JacX on 2005-04-21
OK So I installed UBUNTU on a machine with the following installations....

HD1 - Windows 98 (Primary Boot Drive Containing MBR)
HD2 Partition 1 - Windows XP
HD3 Partition 2 - Ubuntu

GRUB loads windows 98 and Ubuntu but not XP it just throws up an error even though it detected it during installation.

Any Ideas???

---

### Post by erkki70 on 2005-04-21
Hi,
Could you post the exact error you get and your /boot/grub/menu.lst file so people can surely help better.

Cheers,
Erkki

---

### Post by JacX on 2005-04-21
Yeah sorry I will try.

To be honest I had to reinstall mandrake as it installs lilo on the MBR which detects all of the drives and partitions first time.  The girlfriend really need to access the xp partition.

I will try reinstalling tonight and if the error persits I will post the error message

Cheers

---

### Post by cjm on 2005-04-21
the same thing happens to me on any machine when installing sarge or ubuntu on top of a dual win boot setup.

this link really helped me out:

[http://lists.debian.org/debian-boot/2004/06/msg01051.html](http://lists.debian.org/debian-boot/2004/06/msg01051.html) 

just boot into your working win partition ( win98 ) and rewrite the boot.ini file as described in the post.

hope that helps...

warning.... this has worked 3 out of 4 times for me.   one time both win partitions became unbootable.

---

### Post by JacX on 2005-04-28
Cheers for the link I will play tonight!!

---

