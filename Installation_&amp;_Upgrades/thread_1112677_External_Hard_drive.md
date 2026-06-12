---
title: "External Hard drive"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by error919 on 2009-03-31
My friend recently got an external hard drive. He 
asked me for my ubuntu live cd to install ubuntu
on the hard drive. I told him the instructions I
read on how to install.
1 boot from live cd.
2 disengage/eject the internal hard drive.
3 install to external hard drive as normal.

but now I am wondering if grub will be installed.
I just want to know If i will have to fix it for
him.

---

### Post by sgosnell on 2009-03-31
There is no need to remove the internal HDD, as long as you're careful.  The internal drive will be sda, and the external drive will be sdb, or another letter later in the alphabet, depending on what else is connected.  The bootloader will be installed, but the installation location depends on the conditions.  If there is no other drive, and you're installing to sda, then it will obviously go there.  If you leave the HDD, and install to sdb, then at the last window, just before you click on the final Install button, click on the Advanced button, and instead of the default (hd0) select (hd1).  (hd0) is the first drive, and (hd1) is the second drive.  Just make sure you know which drive is which.

---

### Post by error919 on 2009-04-01
If the internal hard drive is ejected does it 
install by default to the external hard drive then?
What about grub?

---

### Post by Mark Phelps on 2009-04-01
It has to install GRUB somewhere -- so if the only drive connected is the external drive, it will install it there.

---

### Post by sgosnell on 2009-04-01
Yep.  If the external HD is the only drive connected, then that's where it will be installed.

---

