---
title: "How well will this Dell laptop work with Ubuntu?"
date: 2005-01-07
forum: Hardware &amp; Laptops
---

### Post by Spif on 2005-01-07
Dell Latitude D800:

Intel® Pentium® M Processor 1,7 GHZ
15.4" WXGA (1280x800)
nVidia® GeForce™ 5650 128 MB
40GB ATA-100 harddisc
512MB 266MHz DDR RAM (2x256MB)
Integrated MiniPCI Wireless 802.11
Integrated 10/100/1000 Ethernet LAN
Integrated 56k V.92 modem
Dualpoint (Touch pad & Track stick)
Integrated Bluetooth card
8x DVD / 24x CD-RW Combodrive
Lithium Ion 9 cell batteri with ExpressCharge 

Before I buy this laptop I want to be completely sure it works perfectly with Ubuntu. Has anyone tried running Linux on a computer with more or less the same specifications as above? 

Thanks in advance!

---

### Post by Spif on 2005-01-09
Anyone?

---

### Post by fng on 2005-01-09
Maybe there isn't anyone here with the same specs :(
Did you allready google for it?

This came up:
[http://cs-people.bu.edu/artdodge/linux/d800/](http://cs-people.bu.edu/artdodge/linux/d800/) --> debian specifique
[http://ds9a.nl/dell-d800/](http://ds9a.nl/dell-d800/)
[http://www.mikehardy.net/linux_latitude_d800/](http://www.mikehardy.net/linux_latitude_d800/)

---

### Post by Krash1201 on 2005-01-09
the d800 is similar to the 8600, which is what i run ubuntu on right now.  install was easy, recognized the and installed the laptop support no problem.  when you load the 686 kernel it smokes.  you will start to run into problems with the wireless networking, but the gigabit ethernet should run out of the box.  dell ships broadcom chipsets with their laptops under the dell truemobile psudonym.  the cards are great with windows, but they are not yet supported in linux.  ndis wrapper fixes this problem, but you need to make sure you load the kernel source, and use an older windows driver that you can get from support.dell.com.  check out [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) and follow the directions to the T including the version of ndis wrapper and specified .inf file from the correct file in the unzipped driver.  that said, my dell runs like a champ.

---

### Post by Spif on 2005-01-09
Thanks! Exactly what I was looking for :D 

> when you load the 686 kernel it smokes.
WHAT?!? Are you serious? 

I’m completely new to Linux, so could someone please make an idiot-proof tutorial on how to install this ndis wrapper? Please..? I would hate to have my new computer melt down right after I bought it…

---

### Post by theBlackDragon on 2005-01-11
[QUOTE=Krash1201]when you load the 686 kernel it smokes.  you will start to run into problems with the wireless networking, but the gigabit ethernet should run out of the box.  [/QUOTE]

1. In what way does it smoke? I haven't had even the slightest problem yet (alos Dell Lattitude d800 here)
2. Yups, wireless is a pain in the a** works like a charm on Gentoo though...
3. Why would you need all those ndiswrapper tricks if you state that gigabit network works out of the box? :confused:

---

### Post by oberon on 2005-01-11
With Dell just be careful.  They generally use Hitachi (IBM) Travel Stars, occasionally you will see a Seagate or Toshiba drive.  With the Hitachi's my company has a 20% failure rate in the first two yeas (this is with the Dell D-series laptops), with over 8,000 laptops.  When they are working they are generally a decent machine.  My personal opinion is that Dells are trash, but that my personal some what biased opinion.

---

### Post by theBlackDragon on 2005-01-11
[QUOTE=oberon]With Dell just be careful.  They generally use Hitachi (IBM) Travel Stars, occasionally you will see a Seagate or Toshiba drive.  With the Hitachi's my company has a 20% failure rate in the first two yeas (this is with the Dell D-series laptops), with over 8,000 laptops.  When they are working they are generally a decent machine.  My personal opinion is that Dells are trash, but that my personal some what biased opinion.[/QUOTE]

I know, I already had my harddisk changed (Hitachi one), but other than that I've  had no problems whatsoever...

---

