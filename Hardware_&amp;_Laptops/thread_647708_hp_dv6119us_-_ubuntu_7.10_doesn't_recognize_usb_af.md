---
title: "hp dv6119us - ubuntu 7.10 doesn't recognize usb after boot"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by fokochang on 2007-12-22
I've been using ubuntu 7.10 for almost a month now. I have it working absolutely perfectly on my hp compaq desktop, which I installed ubuntu second to my hp dv6119us pavillion laptop. 

After following many guides, I have everything working half-wayish. I have my video card working, as well as my wireless. However, I haven't been able to find any good guides on whatever I need to do for my usb not recognizing after boot up.

I've tried plugging in my mouse and flash drive, but neither work unless I restart the laptop.

Thanks in advance, and merry christmas!

---

### Post by fokochang on 2008-01-08
i did a fresh install, and everything worked perfect. the most important thing is to add in during running the live cd, "noapic irqpoll noirqdebug".

which i read from here: [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

i also checked all the extra repositories in software sources, and then updated. the only thing that doesn't work now, is my multimedia card reader, i think. everyone else says it should work out of the box.

---

