---
title: "Persistent screen resolution problem"
date: 2010-02-12
forum: Hardware
---

### Post by tm3508 on 2010-02-12
I installed Karmic a short while back and have been unable to increase screen resolution despite trying loads of suggested fixes.

Resolution is 1024x768 at the moment, I want to change to 1280x1024, which is undetected.  Hardware is AOC LM720A LCD monitor, Gigabyte 6600GT AGP using NVidia 185 driver.  I *should* be able to get 1280x1024 because it works in XP.
Monitor spec:
[http://en.kioskea.net/guide/details/109653-aoc-lm720a](http://en.kioskea.net/guide/details/109653-aoc-lm720a)

System > Preferences > Display gives an error - graphics driver doesnt support this tool, suggests using NVidia  tool.
NVidia settings tool has resolutions 1360x768, 1152x864, 1024x768 and below.
Ive tried editing xorg.conf, but I always get an unable to parse file error when I reboot.
Ive tried xrandr, but get a failed to change screen resolution error when I try 1280x1024 modes

If I can get my monitor to be recognised, maybe the normal fixes will work?  As I said xorg.conf changes havent been successful though.  I have an XP driver for the monitor, no Linux ones are available to my knowledge.

---

### Post by ScarySquirrel on 2010-02-21
A user named jeanseb asked the same question in the Linux Mint IRC server.
He has an NVIDIA 9600 GT.
His desired screen resolution is 1650 by 1050.

---

