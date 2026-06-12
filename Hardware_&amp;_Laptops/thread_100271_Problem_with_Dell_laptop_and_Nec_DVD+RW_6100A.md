---
title: "Problem with Dell laptop and Nec DVD+RW 6100A"
date: 2005-12-07
forum: Hardware &amp; Laptops
---

### Post by WebDrake on 2005-12-07
Hello all,

My Dell laptop (Inspiron 8600) comes with a Nec DVD+RW 6100A drive, and it doesn't seem to be working properly with Breezy.  First of all, CD playback is very skippy and poor---it seems like the Gnome CD player is having difficulty reading the disc properly, although it works fine under Windows XP.  In addition, when I try pressing the tray release button on the drive, to change disk, there is no response!  Again, Linux-only problem.

Can anyone advise on a method to check what hardware Ubuntu thinks I have, and how to correct it if the setup is wrong?

Many thanks,

         -- Joe

---

### Post by daller on 2005-12-08
Have you got DMA enabled?

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

run this for identification:

```
sudo hdparm -I /dev/hdc
```

...where hdc is the drive!

---

### Post by WebDrake on 2005-12-08
Hmm, seems to have fixed things.  Thanks very much! :-)

---

