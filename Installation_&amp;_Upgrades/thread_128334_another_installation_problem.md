---
title: "another installation problem"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by jessie_gabor1213 on 2006-02-11
Hello,
I'm trying to load ubuntu breezy onto a windows xp pro system, a dual boot situation. I'm fairly new to linux so this may be a simple fix. When I pop the install cd in and boot, it brings up the right start up screen, but no matter what mode I try to install in (default, expert, whatever) it acts like it's loading a bunch of stuff for about 10 seconds, and then the screen goes black and stops running.
I also tried the live cd just to check, and the same thing happened with it.
Any suggestions are appreciated!

---

### Post by taurus on 2006-02-11
Could be a number of things like problems with your CDs, hardwares, video card, monitor, etc.  However, did you download the CDs or did you receive it from someone else?  If you downloaded and burned them yourself, make sure you run the md5sum first (especially if you downloaded them under Windows) and burn them at a slow speed like 4x instead of default value!!!

---

### Post by jessie_gabor1213 on 2006-02-11
I got the disks straight from ubuntu, but earlier I also tried burning one myself and it did the same thing.

---

### Post by taurus on 2006-02-11
See if you can boot the same CD from another computer!!!  If it boots okay, then there is something wrong with the graphic card then...

---

### Post by arckeda on 2006-02-11
if it frezes try:

live noapic nolapic

---

### Post by jessie_gabor1213 on 2006-02-12
I won't be able to try it on another computer until tuesday... is there anything else that anyone knows of that I could try?

---

### Post by jessie_gabor1213 on 2006-02-12
also (this may be an unbearably stupid question, but...) if something were wrong with the graphics card, why would the computer work ok with windows, and why would it show the initial linux install screen?

---

### Post by greateastern on 2006-02-12
Sounds like the problem i had as well. I can get so far with Hedghog but Badger gets really stuck. Any help would be appreciated here also.

Andy

---

### Post by jessie_gabor1213 on 2006-02-13
for those of you who may have also had this similar problem, just thought I'd let you know that I fixed it by using the parameter "vga=771"
Hope it works for you!

---

