---
title: "swap isn't active on its own"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by timmytron on 2007-05-29
ok, this might not be the right place for this, but i recently updated my kernel and my swap disappeared. i have remedied this for the time being, but every time i restart, i have to "re-activate" it. any way i can not have to go through that step every time?

---

### Post by Tilo on 2007-05-31
you need to add the correct line to /etc/fstab to let the kernel know where the swap space is.

Is the swap partition still there?  e.g. type:

fdisk -l /dev/sda   (or whatever your harddrive device is)

do you see the swap-partition? 

If yes, add this line to your /etc/fstab file:  

/dev/sda2    swap   swap   defaults  0 0 
^^^^^^
this needs to be the correct partition


If you really lost your swap partition (e.g. it is not listed by fdisk), you can also add a swap-file
on your root-partition, and add that swap-file to /etc/fstab -- this way your OS swaps into a file.
Less efficient, but at least you can swap.

---

