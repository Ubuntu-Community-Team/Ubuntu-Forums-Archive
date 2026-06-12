---
title: "Random  hard lockups - Any ideas?"
date: 2008-08-01
forum: General Help
---

### Post by bholliday72 on 2008-08-01
Hello,

I've been using Ubuntu for a while now, and I love using Ubuntu when my computer doesn't completely lock up.  I've tried the 32 and 64 bit versions and the 64 bit JUST locked up on me for the first time.

The 32 bit version seemed to have the problem way more than the 64 bit.  It used to happen just about every time I installed flash on 32 bit, but I tested out a theory of not installing flash and it still locked up.  The 64 bit edition does have flash 9 installed and it was working fine for about three days.

The hard lockup problem just happened a few minutes ago.  Was playing around with Compiz Cube and had a few basic windows (Firefox, Thunderbird) open on different workstations when it happened.  I did a google search and went to click on a link when the mouse stopped moving, and my keyboard flashed the num lock, caps lock, and scroll lock over and over again.

I would love to switch from Windows to Ubuntu permanently, but Windows does not lock my computer up, and Ubuntu (32 and 64) do.

My specs:

Intel Core 2 Quad Q6600 (overclocked to 3.2 GHz with proper cooling)
Gigabyte GA-EX38-DS4 Motherboard
2 GB PC 6400 Corsair memory
250 GB SATA II Seagate HDD
Samsung OEM DVD burner
eVGA Geforce 8800 GTS (512 MB, G92)
Linksys WMP54G PCI Wireless adapter
Visiontek TV Wonder HD 650 PCIe (doesn't work on Ubuntu, just listing it)
610W PC Power and Cooling PSU

My only theory is that the video card is overheating.  The temps are a little high at idle (~72C) but I don't have that issue in Windows because I can manually turn up the clock in Rivatuner.  Doing research on Ubuntu tells me that adjusting the video card fan speed is not yet possible.


Any help would be greatly appreciated. :popcorn:

---

### Post by bholliday72 on 2008-08-01
bump

---

### Post by bholliday72 on 2008-08-03
I still have this issue.  I am still a beginner with Ubuntu, so the problem can't be caused by having the wrong software packages installed (right?).

I am using the most current video driver (evga Geforce 8800 GTS 512 G92) that Ubuntu can get when it automatically grabs it off the net.  I've tried using EnvyNG with 32 bit Ubuntu and still had the hard lockup issue.

This is really a bummer, as I would love to be able to use Ubuntu consistently with the Compiz Cube and 4 different workstations to rotate through.:-({|=

---

### Post by bholliday72 on 2008-08-03
bump Help!!

---

### Post by bholliday72 on 2008-08-04
It even seemed to happen when not using proprietary graphics drivers / compiz / desktop effects.  I have deleted the partitions containing 8.04.1 and I'm going to try out 7.10 Gutsy and see how that goes.  Thanks.

---

### Post by drake22 on 2008-08-04
I am having a similar issue! I am using Ubuntu 8.04. Same gfx card (512mb 8800 GTS), but with an AMD X2 2.4ghz dual core (4200+ i think). Worked fine in Windows but I wanted to switch to Linux.

It first happened while playing WoW using Wine. I figured it was just because I tried playing a Windows game and I ignored it. It has since happened a few times while playing native Linux games. Last time it happened was while loading FlightGear. My system locks up and the caps and scroll lock lights flash on and off, requiring a hard reboot. It is completely stable as long as I do not run any games, had the computer on for about 24 hours or so without a single lock up.

Please someone help me! Thanks.

David

---

### Post by dentaku65 on 2008-08-04
In my case was a problem of temperature and the CPU for this reason was freezing the machine.

Fortunately in the BIOS I'm able to lowering the CPU clock from 200MHZ to 100MHZ, put the speeding fan continuously and every 1/2 seconds.
For now the machine is ok, not freezing anymore.

---

### Post by bholliday72 on 2008-08-04
I tried to install 7.10 x64 Gutsy today and it won't install properly.  When I use start / install ubuntu the screen shuts off for ~30 seconds and turns back on at a black screen, x does not start.  same thing happens in 'safe graphics mode'.

I have a feeling that Ubuntu will be awesome as soon as nvidia develops a driver that enables users to mess with the fan speed setting.

EDIT: Solved.  Downloaded and learned how to use nvclock.  Now I'm cooking with Ubuntu!

---

