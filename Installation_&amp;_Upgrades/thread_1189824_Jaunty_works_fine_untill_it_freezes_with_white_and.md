---
title: "Jaunty works fine untill it freezes with white and blue screen"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by AmsterdamMack on 2009-06-17
Hi,

I'm new here and not so sure if I'm in the right thread - so please feel free to move this to a better location :-)

First my hardware: 
AMD Athlon 2650e 2.26.1 Ubuntu 2009-05-06 Kernel: 2.6.28.113-generic 1GB RAM (64% Free) Geforce 6150SE nforce 430

When I tried to install ubuntu 8.10, I had exactly the same kind of crashes that I experience now. The screen went white and blue and I can not get any access anymore. No other control no x-server restart - completely frozen. With a bit of research (I was thinking about the combi AMD / nvidia onboard) I found a thread that helped me.

The only thing I had to adjust to make 8.10 work, was removing **powernod** in synaptics and the machine was running without any problem for months and months.

Now after upgrading to Jaunty the machine freezes again and I don't know why. :-(
Sometimes I can boot and work for hours sometimes it freezes during boot, sometimes while surfing. :-|

I'm a newbie and need some help. What files could give me an idea to find out what's going wrong here?

Thank you very much in advance!

McMack

---

### Post by AmsterdamMack on 2009-06-18
Hi, 

I switched off every powersaving related thing available from GUI side. Screensaver on black no Open GL. Compiz off. NVIDIA driver switched off. Udate done. 

I was using lst.fm to monitor how long the uptime would be ;-)
PC was running from 11 last night till this morning 7.15 but than again totally frozen. Arghh

Anyone more ideas?

McMack

---

### Post by metiosarius on 2009-06-18
Have you tried removing the program/line/etc. that you removed in the previous version that fixed the problem?

---

### Post by AmsterdamMack on 2009-06-18
Hi metiosrius,

thank you for your response. That was my first thought too, but the POWERNOW package was not installed with the upgrade. 

McMack

---

### Post by AmsterdamMack on 2009-07-20
Mhh - I don't have any evidence, but since I changed the amarok setting to not automatically scan folders for changes it seems to be ok...
So maybe only the collectionscanner stumbled over some faulty mp3's or so.

McMack :D

---

