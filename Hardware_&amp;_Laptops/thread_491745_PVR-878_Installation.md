---
title: "PVR-878 Installation"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by poco153 on 2007-07-04
Hello everyone.

I have installed Ubuntu 7.04 on an older system (Athlon XP 1900+, 512MB, GeForce 4 440MX) with the hopes of making it into a passable DVR.  I came upon a KWorld Xpert TV - PVR 878.  I did a bunch of research, got MythTV installed (this is my first true Linux install), and decided that the PVR878 was indeed compatible with Ubuntu based on the number of people who had posted that theirs functioned.

I, however, cannot get it to work.  Following instructions found on a few sites, I created a file called bttv in /etc/modprobe.d/ containing the text "option bttv card=78 radio=1 tuner=38 pll=1 gbuffers=4 gpiomask=0x1c0007 audiomux=0x080000,0x000001,0x080000,0x080000,0x000001"

I then rebooted, but I still cannot get MythTV's backend setup to find a suitable card.  When I open System > Preferences > Hardware Information, the card shows up as two pieces: "Bt878 Video Capture" and "Bt878 Audio Capture"

How do I, well, make Ubuntu play nice with the card and let me watch and record TV?

Thanks,

---

### Post by poco153 on 2007-07-06
An Update:

I got video working and MythTV is all fine and well except that I do not have sound in any form while MythTV is running.

I have the Bt878's audio out plugged into my sound card's input.

---

