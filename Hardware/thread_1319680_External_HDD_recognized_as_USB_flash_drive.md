---
title: "External HDD recognized as USB flash drive"
date: 2009-11-08
forum: Hardware
---

### Post by Micro_s on 2009-11-08
I'm not sure if I can express my self understandably.
When I plug in my external HDD Western Digital My Passport, system treats it as USB flash drive. On desktop it shows flash disk icon, but that is not the main problem. The problem is when umounting it (Safely remove). The drive is umouted alright, but it is still turning and I must wait about 15 minutes until it stops.

I found help in using:
sdparm --command=stop /dev/sdb
but it is annoying to run the command every time I want to unplug the external HDD. And it is not sbd every time. And if I use UUID it works only for my disk.

I suspect the system that it treats the external HDD as USB flash drive so it sees no reason for stopping it.

Is there a way how can I tell the system that I plugged in an external HDD and it needs special attention?
Or is there a way how can I attach the sdparm command to Safely remove?

Thanx.

Kubuntu 8.04 64-bit on Dell Vostro 1700, external HDD Western Digital My Passport Essential WD500ME

---

### Post by darkshadow on 2009-11-08
As far as I know all external hard drives connect using USB mass storage so it is normal for it to show up like that. I think Windows just handles large sizes different and treats them like a internal hard drive. My personal external shows up as a flash drive in Linux and Windows XP but as a hard drive in Vista and 7.

As for it still spinning that is probably normal to since even though it is not mounted it is still running at least until it goes into low power mode after extended inactivity.

---

### Post by Micro_s on 2009-11-09
And is there a way how can I make sdparm command run every time the external drive (recognized somehow... maybe uuid) is umount?

---

