---
title: "getting an added device to stick...."
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by spacemonkey on 2005-07-19
So I finally found a way to get my gameport Gravis GamePad to work on Ubuntu.  I followed the instructions I found on the justlinux forum, located here: [http://www.justlinux.com/forum/showthread.php?t=40856&highlight=gravis](http://www.justlinux.com/forum/showthread.php?t=40856&highlight=gravis) 

My question is this however:

How do I get the results from the commands:

mknod input/js0 c 13 0
ln -s input/js0 js0


to stick in the /dev directory after a reboot.  Every time a reboot my PC, I have to re-add js0 to /dev/input and make a link in /dev.

---

### Post by spacemonkey on 2005-07-20
there's got to be a way to do this.  Anyone??

---

