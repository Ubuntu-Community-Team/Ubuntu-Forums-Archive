---
title: "SATA Raid Recommendations"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by Plagued on 2005-07-27
Hello all,
  I am looking for recommendations for a hardware SATA RAID controller that can do a RAID 5 and works well in Ubuntu. Here are some hardware specs:

Dual Xeon 2.6
4GB RAM
TYAN S2668 Tiger i7505 motherboard

And here is the situation. This is for work, so I figure that I may be able to spend as much as $400 for a SATA RAID card. I have a database that I have to house on my workstation for a while. The database will require very little access (which is why it isn't getting it's own server right away), but since it is quite important and took me substantial time to build, I would like to run a RAID. The machine is currently running Gentoo without any kind of RAID. The motherboard has an onboard SATA controller that supports RAID 0 & 1, but it only can handle 2 drives. My manager has told me that she does not want me setting up a software RAID (and I have my own reasons for not wanting to), but she would be agreeable to a hardware RAID.

I am contemplating switching to Ubuntu b/c I have had excellent luck with Ubuntu on my work laptop, and 2 personal laptops, as well as my personal desktop and have found nothing that I can't do in Ubuntu that I can do in Gentoo. Since this move to a RAID configuration would involve a complete rebuild of my system, Ubuntu would be a much faster solution. (I generally figure a full day of downtime when I re-install Gentoo).

So my questions are these:

1. Is it possible to boot Ubuntu from a Hardware RAID 5? (No dual boot ... pure linux system)
2. Does anyone have any recommendations for a hardware SATA RAID controller that can do RAID 5, handle at least 3 drives (5 - 6) would be prefereable, and works in Ubuntu?

---

### Post by Gog on 2005-08-22
Plagued, did you get anywhere with this project? I'm trying to find a well supported raid5 card myself....

---

### Post by heimo on 2005-08-22
You guys want to check what 3ware has to offer. That's the way I'd go. It's been time since last time, so no specific model numbers (I believe I had 7000-series). Sorry, no other answers. Don't know about booting from raid5.

---

