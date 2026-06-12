---
title: "I need to get Grub back"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by jmagick07 on 2009-01-07
After years of just using Ubuntu, I decided to partition my hard drive and install Vista.  On Vista I tried EasyBCD but it isn't working for me.  I would really just like to get Grub back like how it was before, and use Grub to decide which OS to boot into.

How do I get it back?  I hate that it directly boots into Vista everytime I start up my laptop.

---

### Post by tsger on 2009-01-07
Try these intstructions: [http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by 2hot6ft2 on 2009-01-07
to restore Grub to your MBR, so if you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:

sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

And that's all it should take.

---

