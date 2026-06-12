---
title: "dual boot problem"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by MrCanuck on 2009-10-23
Hello.

I am so happy that i finally got the time to back up my Vista system, reformat the drive and install Ubuntu on my laptop.  ubuntu is working great, and so far so good.

I would however like to have Windows XP on here, as a dual boot.

So i loaded up the Ubuntu live CD, changed around the partitions, and began to install XP......XP is now installed and i booted into it.

I then of course could not get back into Ubuntu, so i read some articles and with the live cd i was able to install GRUB again and get back into my Ubuntu.

But now i cant get into XP (funny i know).  

/dev/sda1 has my Linux instalation.

/dev/sda2 has my XP Instalation

/dev/sda3 and /dev/sda5 have my boot information i think.


I am a linux Noobie and don't know a lot about the Terminal in Linux and all that stuff.  If some one could please explain to me how to get both operating systems to show up at startup that would be great (explained in simple form plz)

Thanks.

---

### Post by earthpigg on 2009-10-23
hi!

towards the bottom, this tutorial walks you through the process of getting Windows in GRUB.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by earthpigg on 2009-10-23
pay special attention here at the end of that tutorial:

> Note that you should also verify that hd0,0 is the correct location for Windows. If you had installed Windows on the 4th partition on the drive, then you should change it to (hd0,3)

grub starts counting at zero, not 1.

for you, i ***think*** that means your windows partition is what GRUB would call (hd0,1).

also please note i am assuming you are talking about ubuntu 9.04 or earlier. 9.10 uses a ***completely different*** version of GRUB and these directions will not apply.

---

