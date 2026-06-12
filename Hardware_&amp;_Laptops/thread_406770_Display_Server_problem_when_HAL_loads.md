---
title: "Display Server problem when HAL loads"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by doml25 on 2007-04-11
I have Windows XP Pro installed on my Dell Inspiron 8600 Laptop. I was not able/willing to mess with repartitioning the hard drive to install Linux. So I swapped my XP hard drive for a blank one and installed Ubuntu 6.06 LTS on the blank hard drive. 

Now I pull out my XP hard drive and insert my Ubuntu Hard drive when I need to use Linux. (Not the best way but I spent a long time getting this far) 

Everything was working perfect UNTIL: 
1.	My laptop cover was closed and I pulled out my XP hard drive and put my Linux hard drive in.
2.	I opened my laptop cover to turn it on and I saw my XP screen flash on the monitor and then my computer shutdown.

The problem is that I thought my laptop was turned off but it was in standby mode when I switched the hard drives. (go ahead and laugh, I would be, if I had the time to play with it) : )

Now everything seems to work fine in XP and fine when I boot to my LiveCD (mounted on USB stick)

But, when I swap my XP hard drive for my Ubuntu drive and try boot, it appears to be alright until HAL starts to load. Once that happens I get dumped to a terminal prompt (tty). My monitor flickers periodically and after a while I get a message to the effect of “The display server has shutdown 6 times in the past 90 minutes.” 

Any ideas on how to fix this without a complete reinstall? Linux appears modular and I should be able to replace a damaged file or two or change some settings somewhere. 

I read some posts about changing settings in my xorg.conf file but these settings where working perfectly before.

DomL25

---

### Post by doml25 on 2007-04-11
Some more information.

I attempted to boot in rescue mode and made it up to the point where the last line loaded said something about setting up per-vc fonts, then it dumps me to the tty terminal. Anyone know what vc fonts are? 

I installed Ubuntu on another partition of the hard drive and it works perfect. I then compared the xorg.conf files and they are neraly identical. I also compare the xorg.0.log files. They are also very similiar both reflecting the same errors. (wacom errors I believe these are related to the synaptics touchpad) So the problem does not appear to be part of xorg.

doml25

---

