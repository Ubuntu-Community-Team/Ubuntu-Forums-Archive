---
title: "Blank screen on normal boot"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Everett Lethe on 2009-04-15
Xubuntu 9.04 blank screen on normal boot

On Dell Dimension 2350, Intel Celeron Northwoods 2.2 Ghz, 1GB RAM, Intel 82845G/GL/GE/PE/GV Graphics controller:

Normal cold boot leads to blank screen (no cursor)

Recovery boot, choose "xfix try to autofix graphics problem" then boot and Xubuntu desktop loads fine with "Display" (under Settings) showing Screen 1 with resolution "1024x768" with 75Hz refresh rate.

Display continues to operate normally on Restart. HOWEVER after shut down and cold boot, same problem all over again.

QUESTION: How can I set the system permanently the way "xfix" does to make the display function?  (I have tried editing xorg.conf as suggested elsewhere without success)

If it is not obvious from this message, this is the first time I have installed a Linux-based OS.

Thank you for any advice about this problem.

---

### Post by gloomyfeet on 2009-04-26
Unfortunately I have no advice, but have a similar problem with Xubuntu 9.04 on an old NEC laptop (Versapro VA65H, Pentium III 650 mhz, 384mb ram, S3 Twister graphics chipset). 

On cold boot I see the Xubuntu screen and progress bar, but after the progress bar fills it goes to a black screen no cursor, and no disk activity. Ctrl-Alt f1/f2/f7 have no effect.

Running xfix has no effect in my case. I can sometimes (but not always) get a short-term fix by booting into recovery mode, opening the root shell and running "dpkg-reconfigure xserver-xorg" (no quotes). After answering "OK" to all the questions (most of which concern keyboard layout) and going back to the recovery menu, I can resume startup and get into the gui with no problems. However, if I restart or cold boot, the black screen returns.

Xubuntu 8.10 behaves identically on this machine, but 8.04 works fine.

---

### Post by mingle on 2009-04-26
Hi, 

I have comparable GFX issues on my Compaq Evo 510 SFF, which has intel GFX also.

Like you 8.04 was fine, but 8.10 and 9.04 have problems.

It's a prime PITA...

Cheers,

Mike.

---

### Post by vatsok on 2009-10-15
Try adding the "xdrvr=vesa" boot option.

---

