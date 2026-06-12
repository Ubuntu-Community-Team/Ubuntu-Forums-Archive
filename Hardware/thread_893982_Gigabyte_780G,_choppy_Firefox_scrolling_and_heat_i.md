---
title: "Gigabyte 780G, choppy Firefox scrolling and heat issues"
date: 2008-08-18
forum: Hardware
---

### Post by Skuzniak on 2008-08-18
I built an HTPC a while ago, but have decided to convert it to my primary computer after my father's old clunker finally bit the dust and he "inherited" my desktop. The motherboard is the Gigabyte 780g mATX, and, under XP, ran fairly well. Being that it is now my primary (and only) computer, I decided to install Ubuntu and attempt to leave XP in the dust. However, I have encountered two problems that are prohibiting me from purging the Microsoft from my existence:

First of all, Firefox scrolling is choppy. It is quite similar in nature to the choppiness experienced when using a Windows computer and attempting to scroll through a webpage in Firefox with no video drivers installed, although to a much smaller degree. It is just bad enough to consider returning to XP, but I would much prefer to remain with Ubuntu.

For my second issue, the integrated GPU (780G, or HD3200 if you prefer) is significantly hotter under Ubuntu than XP. With window effects disabled and idling at the desktop, the heatsink for the integrated GPU is close to 10 degrees Celcius hotter under Ubuntu than XP. Temperature sensors have never been able to give an accurate reading for the 780G IGP (most usually peg it at 80 degrees, no matter if it is loaded or idling), but the thermometer to the heatsink very rarely lies.

Based on my (limited) experience, both of these problems sound like a driver issue. The ATI binary X.Org driver is installed, as is the fglrx propietary driver. Thinking that there may be conflict between the two drivers, I attempted to uninstall the X.Org driver. Upon rebooting, I was greeted with a low-grahics-mode Ubuntu; reinstalling the X.Org driver resolved this temporary crisis. I am still unsure if these two drivers are conflicting; reading their descriptions indicate to me that they handle different functions. The X.Org driver handles 2D and accelerated OpenGL, while the fglrx driver handles accelerated 3D.

Is there anything that can be done to resolve these issues? Thank you in advance.

---

### Post by Skuzniak on 2008-08-19
As an additional issue, I seem to be having trouble with audio over HDMI. The HDMI output appears under Sound Preferences, but has no mixers (like Master, PCM, front, rear, ect) under it's dropdown. Every other sound device has atleast 1. Setting the output device to the HDMI out and using the "test" button doesn't result in any sound, while the standard speaker output does.

---

### Post by prince_niceguy on 2008-09-15
I too have same config and mine runs quite cool. I think it might have to do with some Xorg settings. I tweaked with the [following link]("http://gentoo-wiki.com/HOWTO_ATI_Drivers") and it is working like charm. I disabled desktop effects as mine is htpc and I do not need any desktop effects. So, disabled composite in the xorg.conf.

Hope that helps.

---

### Post by brickheadbs on 2008-09-20
I fixed my sound problem of no optical link audio by opening the volume control (double-click the speaker icon), change device to HDA ATI HDMI, and putting a check in the box that says IEC958. At least I think this fixed it... afterwards it didn't matter whether its checked or not.  Either way...lots of clicking worked.  Let me know if that does for you.

I also have the firefox issue, it seems to hang/crawl a lot.  My mouse scrolls super smooth in XP, but choppy in Ubuntu.

Dunno about my temps, but I do know that flash videos aren't playing well (hulu.com)  Again, fine in XP.

The cube in Compiz Fusion scrolls a little choppy on the edges even though the the chip has no trouble keeping the frame rate over 35...

Linux's only downfall is drivers!!!  We need a genious to solve that problem.  I think Linux would take off a lot more.  I'm a geek and it annoies me... no way would a "average" user be patient enough.  The automatic offer to install ATI's drivers was a nice change.

Woe...did I cover a little too much ground with this post?

---

### Post by elanthis on 2008-09-21
There's absolutely no acceleration support for 780G right now, hence the choppiness.  The heat issue is probably due to a lack of power  management support for 780G.  Just wait, the drivers are being worked on.

---

### Post by kevbeck on 2008-09-30
Would that be the RadeonHD driver?

Phoronix told me that the 780g chipset was at least partially supported by RadeonHD:

[http://www.phoronix.com/scan.php?page=article&item=radeonhd_780&num=1]("http://www.phoronix.com/scan.php?page=article&item=radeonhd_780&num=1")

Is this not applicable to the Gigabyte board?

---

### Post by travm on 2008-10-10
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Follow_These_Instructions_Carefully](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Follow_These_Instructions_Carefully)
Use Ati driver, catalyst 8.9 for linux
I have same motherboard, and dude, seriously.  3d performance rocks.  You NEED this driver.
follow the guide above.  for me some things didnt go smoothly, thus I updated the wiki.  I still havnt been able to abandon XP, though i am on the brink.  Frankly i just need it to be able to record my shows, and play movies for me as well as XP can.  ATM that is a work in progress.
PM me or something if you need more help.

---

### Post by vs8 on 2009-02-07
Intrepid is very, very choppy in my PC. I have a Gateway GT5676 with AMD's 780g chipset. Like you said Firefox's scroll is very choppy and the overall experience is slow.

I also had problems with the processor. Whenever I listened to music with any media player the processor had this "little burst" it went at 100% and then down to 14-15% in an instant and that made Ubuntu freeze for a couple of milliseconds. High resolution flash videos were almost unplayable because of the choppiness. When I watched videos I had to turn compiz down because the screen started to flicker. I found a "fix" with gsreamer-properties command and changed a video setting that would let me watch videos with compiz on, but it was extremely choppy.

In conclusion, Intrepid Ibex in my PC is pure garbage. What I did is to go back to Hardy Heron and installed everything as I had it and now everything works perfectly. Everything is super fast and flash works extremely well and stable.

---

