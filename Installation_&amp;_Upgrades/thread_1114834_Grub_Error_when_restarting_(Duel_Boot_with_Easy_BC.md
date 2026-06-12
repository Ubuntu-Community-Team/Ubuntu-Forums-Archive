---
title: "Grub Error when restarting (Duel Boot with Easy BCD)"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by Ubersci on 2009-04-03
I am quite new to Linux and recently installed Ubuntu 8.10 on my second hard drive, which i duel boot with Vista Home Premium. I used Easy BCD to manage my bootloader. I installed grub to the second HDD but now when i boot into Ubuntu it comes up GRUB error, i use the Live CD to repair it through the terminal window and then restart, this works fine and i can use it. But when I shutdown and try using ubuntu later or after being in windows I get the grub error again and I have to do the same thing again with the live cd. Can anyone help me please?

---

### Post by ronparent on 2009-04-03
Does the grub error have a number?

---

### Post by Mark Phelps on 2009-04-03
Please be more specific regarding the "GRUB error".  There is a known problem with dual-boot systems (Vista and Ubuntu) where Vista actually wipes out some of GRUBs files when you boot back into it. I know -- this has actually happened to me more than once!

The fix involves reinstalling GRUB in a special way -- such that Vista can't overwrite it anymore.  It's a bunch of work -- which you don't need to do if this is not the problem.

---

### Post by Ubersci on 2009-04-04
Thanks for the quick reply. There is no error number just the black screen with white writing, like DOS. 
It says-

[B]Bootpart 2.60 Bootsector(c)1993 -2005 Gilles Vollant [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Loading new partion
Bootsector from C.H.hochstatter
Grub Geom Error[/B]

---

