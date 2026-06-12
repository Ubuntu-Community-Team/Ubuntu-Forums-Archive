---
title: "resize root and move swap partitions"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by Samuel on 2005-10-23
Hi i currently have a 54gb partition for ubuntu 2.35gb swap and 57gb /home partition, as seen in the picture:
[[IMG]http://img435.imageshack.us/img435/4905/gparted2td.th.jpg[/IMG]](http://img435.imageshack.us/my.php?image=gparted2td.jpg)

i would like to resize the root partition to something sensible like 30gb and move the swap partition to the end of it so i can give my /home partition more room
to grow, i tried QtParted and the option to resize was greyed out, i tried the breezy live CD and could resize the root partition but not move the swap as the disk uses it, i tried with the boot parameter : live noswap but it mounted the swap partition anyway.

can anyone tell me how i can do this with the minimum fuss please?
im assuming all would be fine after resizing and moving the partitions, am i wrong to do so?

thanks in advance, Sam

---

### Post by Joe_lurker on 2005-10-24
Run the command '/sbin/swapoff -a' to unmount the swap drives.  Remember to backup any important information before attempting to move/resive partitions.

-Joe

---

### Post by Samuel on 2005-10-24
thanks, gonna give it a try :)

---

### Post by Samuel on 2005-10-24
[[IMG]http://img442.imageshack.us/img442/879/screenshot8ef.th.jpg[/IMG]](http://img442.imageshack.us/my.php?image=screenshot8ef.jpg)

dont try this at home folks :( 

now to reinstall breezy, thank god my home dir was backed up

---

