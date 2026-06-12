---
title: "Compatibility check -- new machine."
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by mivo on 2007-10-09
I'm going to pick up the parts for a new box this week. The computer will only run Gutsy, no dual-boot. Before getting the parts, I wanted to check here if there are any known "problem pieces" in my list. I can still make changes. Ideally, Gutsy should run out of the box. ;)

Abit AB9 PRO, P965 (on board Dual PCI-E Gigabit LAN controller 10/100/ 1000M Ethernet)
Pentium E2140, Allendale, 2x 1600 MHz, 1MB Cache, 800MHz FSB, 64 bit
Zalman CNPS9500 AT Ultra Quiet CPU cooler
Western Digital Caviar RE2 250 GB SATA II hard drive
Samsung SH-D163B/BEBP 16xDVD-ROM (SATA)
Samsung SH-S203N/BEBN 20x DVD+/-RW (SATA)
400 Watt PSU Power Unit ([this one]("http://www.nexustek.nl/nx4090_real_silent_power_supply.htm"))
Teac FD-CR7-000 3.5" floppy disk / card reader combination
XFX Geforce 7950 GT 256 MB DDR HDCP (passive cooling)
3 GB RAM -- type undecided yet.
Internet through a Speedport V500 router, but that one already works.

The monitor will probaby be a Samsung SyncMaster 226BW, though I need to look at it before buying. In any event, it will be a 22" running at 1680 x 1050. There are two optical drives for convenience (DVD ROMs cost barely anything anymore).

---

### Post by mivo on 2007-10-09
No responses either mean that there are probably not going to be any problems, or that I picked exotic parts!  I pray for the former. :mrgreen:

---

### Post by dabl on 2007-10-09
Is that a P965 chipset on your candidate mobo?  There were some issues with the 965 earlier this year -- I don't remember what they were.  You might want to search the forum on "P965" and make sure there's nothing to be worried about. 

Also, for whatever its worth, I blew up a 450W PSU and replaced it with a 650W unit, in the process of building my rig, which is kinda similar to yours.  You might want to consider skipping the first part of my experience .... 

Otherwise your parts pile looks pretty good!

:)

---

### Post by mivo on 2007-10-09
From reading some threads I gather that using an IDE disk with this motherboard is likely to cause problems and requires loading extra modules. With only a SATA drive it "seems" to work. The motherboard is something I can't easily replace because the system is employer sponsored, and the MB is already purchased. ;) (and the CPU, the rest is my choice). I hope that Gutsy does a little better with relatively new hardware.

If all else fails I will put the video card in my current system and wait for fixes. ;)

Will look into a different PSU. I thought that 400W is sufficient for the card and the rest, but if you blew your 450W one, I think I should look for something stronger!

---

### Post by dabl on 2007-10-10
RE: hard drives -- here is a very sweet deal, IMHO:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136011](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136011)

I paid $230 each for a pair of these bad boys about 6 months ago, and that was reduced from their earlier pricing.  They're mature products and the price is falling, but they are high-performance. Put a pair of these on your SATA bus and forget about IDE, and it sounds like you'll be in business with that mobo.

PSU  -- I replaced the burn-out with an Antec Tru-Power Trio 650, and it's been running for a year with no issues.  :)

---

### Post by mivo on 2007-10-11
I made some changes to the setup. The 7950GT from XFX is not really available anymore either in Germany or Finland (the locations where I buy the stuff) and it would take a few extra weeks to get one. I settled for a 8600GTS instead (the noiseless model from MSI), which is a few bucks cheaper, too. It is not as good as the 7950GT, but at least OpenGL 3.0 will support it.

As for the LCD monitor: I ruled out the Samsung models because too many people comment negatively on the uneven backlight. I considered a HP w2207 for some time, but the viewing angles seem poor even for a display with a TN panel. It is also a glossy panel, which enhances colours, but also causes problems with light reflections.

I decided on a NEC LCD225WXM-BK, which is one of the very few 22" models that allow to adjust the height of the display. Almost all others have a fixed height. The viewing angle seems okay, judging by [this]("http://www.prad.de/board/attachment.php?attachmentid=7476") picture) and people remarked on the stable backlighting and the sharp display of fonts. It does not have HDCP, but since I don't plan on connecting a video console to it, that is not relevant (may be for others, though). It has built-in speakers, which I could do without (it's usually those 3W excuses of speakers).

I would probably be happier with a different panel technology, but the only 22" with a non-TN panel is a model from Eizo, and it costs almost $2000. There are some interesting 24" models with VN and S-IPS technology, but prices start at around €700, which is beyond my budget (the NEC is €330). I also don't know if I would lke 1920x1200 on 24".

Not a good reason, but a reason nonetheless: I had several NECs over the past years and I was always quite happy with them.

Still looking into the PSU! :)

---

### Post by mivo on 2007-10-22
Just an update: I could get neither a 8600GTS nor a 7950GT with acceptable delivery times (apparently demand for Nvidia card is high?), so I went with a 8800GTS (the 640 MB model) which, while rather powerful, cost more than I had planned -- it is also more powerful than I really need, but at least it was in store. Yes, I fell victim to impatience! ;) I also swapped the PSU for a model with 500W from the same maker as the originally planned one.

The guy who built the box for me (and shipped it -- will be a few days, I only paid for the components) tried to install the 64-bit version of Gutsy and it apparently did not even boot into the live environment. He did not try the alternate CD and he is not a Linux user. He downloaded OpenSuSE, though, and that worked, all hardware was recognised. So I hope that either his Ubuntu Live CD was defect or that the alternate install CD is needed. As long as ANY Linux distro works, I will be happy (that Abit AB9 board just is not the best choice for Linux, but sponsored by my employer), and I'm confident that I will get Ubuntu to work with it. OpenSuSE would not really be my first choice, but at least I know there is a fall-back plan if everything else goes wrong. Windows is not an option.

The 22" NEC arrived already and I put it on my old box for now. Very happy with it, better than I expected.

---

