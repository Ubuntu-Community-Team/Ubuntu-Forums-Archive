---
title: "s3 Graphics Problem"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by uthturn on 2006-12-23
i have an onboard via/s3g Unichrome Pro IGP. It works but video is choppy and webpages are hard to scroll down on its so choppy and artifacts(i think that what u call em) when i try to move a window around on the desktop. Does anybody what i can do to make it proform better i can't find any drivers for it Thanks for any help:-D

---

### Post by Jussi Kukkonen on 2006-12-23
> **uthturn said:**
> i have an onboard via/s3g Unichrome Pro IGP. It works but video is choppy and webpages are hard to scroll down on its so choppy and artifacts(i think that what u call em) when i try to move a window around on the desktop. Does anybody what i can do to make it proform better i can't find any drivers for it Thanks for any help:-D

It's possible that you need to inform the Xserver how much memory you are using. Some shared video memory systems don't seem to function well without that.

Check how much shared video memory you have set in your BIOS settings (you might even want to increase the number) and then tell X what the setting is-- either by editing the config file or running *"sudo dpkg-reconfigure xserver-xorg"* and answering the questions.

---

### Post by zgornel on 2006-12-24
This should help [http://www.ubuntuforums.org/showthread.php?t=318520](http://www.ubuntuforums.org/showthread.php?t=318520) The driver used in xorg.conf not "savage" but "unichrome"

---

