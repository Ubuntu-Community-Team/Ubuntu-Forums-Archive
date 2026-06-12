---
title: "Hard drive utilities"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by Spr0k3t on 2007-10-02
I just purchased an older laptop which Gutsy works great on, but I believe the hard drive may be failing.  Are there any tools I can use to determine if the drive is indeed failing?

---

### Post by ShogunMaster06 on 2007-10-02
Love him or hate him, Steve Gibson has a really good hard drive utility at grc.com called SpinRite.  It costs money ($89-$100 I can't remember).  I think it is a really good product. ([http://www.grc.com/spinrite.htm](http://www.grc.com/spinrite.htm))

Another option is the Ultimate Boot CD ([http://www.ultimatebootcd.com](http://www.ultimatebootcd.com)).  This has a bunch of tools that can come in handy for various different things and it's free.

I don't have any experience with any native Linux tools.  I'm sure they are out there though.

---

### Post by dabl on 2007-10-02
For a gross (and free) check, you might try a few runs of ```
sudo hdparm -Tt /dev/hda
```  (assuming it is /dev/hda). This will exercise it and output its performance figures.  If you do it repeatedly, over some extended period of hours and days, you should get very close to the same figures for all repetitions.  Make sure the test conditions are the same -- don't have other disk-intensive tasks running while you're testing. If the performance figures vary substantially, that would be "a bad thing".  If it's always about the same, then your fears about it may not be justified (i.e. something else is failing, not the hard drive ....)  :lolflag:

---

### Post by hardyn on 2007-10-02
with the cost of hard disks right now 50-80$ for a 60-100gb model... if you are pretty sure the hard disk is the problem... just replace it... is cheaper than the recommended hard disk software.
or see what can be had on ebay... im sure you could get one for 20$

most hard disk vendors offer a smart/surface check tool free... usually run via freedos bootdisk.

---

### Post by Rob500 on 2007-10-02
Hmm, see if there is a tool to check the SMART.

---

### Post by nick_h on 2007-10-02
The package smartmontools contains a utility to look at SMART data.

---

### Post by Bablefish on 2007-10-02
I know of this pay program that has proformed miracles according to some. It's called Spin Rite and I honestly reccomended this program to this guy who thought his hard drive was dying, he ran this once and let me tell you it actually worked better after than it was new. They even now have a Linux version you can get it at [www.grc.com](www.grc.com)

---

