---
title: "UNR installation doesn't work"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by ieduarte73 on 2009-05-12
Hello,

I just have purchased an Asus eee PC 1000HE, and since it came with M$Win XP Home factory installed, I wanted it to have it dual-booting with Ubuntu Netbook Remix 9.04.

I have downloaded the image and made a live USB using unetbootin, the problem is that when I boot from this USB it stops and throws me to the initramfs command line interface (text based), apparently this is due to a bug in casper, a component for live distributions.

However I need this computer to have both OS's since I am an Ubuntu user I don't feel quite comfortable just using M$Win, and I need M$Win to run some apps that won't run in Ubuntu (not even through Wine).

Any ideas on a workaround to this ?

---

### Post by mikechant on 2009-05-12
I can boot OK on my eeePC 1000 from UNR 9.04
The two differences between how you did it and how I did it are that I used a 2Gb SD card instead of a USB stick, and I used the supplied 9.04 Imagewriter tool (running on my desktop machine) to write the SD card, not unetbootin. You could see if either of these alternatives help (although in theory neither should make any difference).

Also, did you check the MD5 hash for your downloaded image before writing it?

---

