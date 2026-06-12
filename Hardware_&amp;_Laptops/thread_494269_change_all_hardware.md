---
title: "change all hardware"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by ahmed-araby on 2007-07-06
Hello
1- Does i need to do any thing if i changed my computer completely except hard disk  of course and does HAL need any thing to be done ?
2- If i copied the partion ( which i installed ubuntu in it ) to another hard disk :
Do I need to do anything except installing grub ?


Many thanks Ubuntu :D

---

### Post by louieb on 2007-07-07
may have to change the uuid's in /etc/fstab not sure. 
can find the uuid to use by running```
 ls -l /dev/disk/by-uuid/
``` from a live CD.
also may have to run ```
dpkg-reconfigure xserver-xorg
``` to get x working. but other than that things  should work.

---

