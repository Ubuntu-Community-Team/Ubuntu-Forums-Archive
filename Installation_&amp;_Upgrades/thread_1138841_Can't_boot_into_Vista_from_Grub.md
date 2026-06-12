---
title: "Can't boot into Vista from Grub"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by ska8tdude on 2009-04-26
I have a Gateway P-6831FX laptop, on which I installed Ubuntu 9.04 through the alternate installed. My laptop is currently running 2 250GB HDs setup in RAID0. I already had a copy of Windows Vista Ultimate installed before I installed Ubuntu.

I made a 50GB partition in Windows with Partition Magic, and promptly installed Ubuntu on that partition with a guided install. The install process seemed to work just fine, but when I restarted the computer only Ubuntu is listed on the GRUB menu, no sign of Vista.

I'm very new to Linux and Ubuntu so I don't know a lot of the terminal commands but I tried using fdisk -l which provides absolutely no output. When I use sudo fdisk -l I get:

Unable to seek on /dev/sda

So is there anyway for me to boot into my Vista installation?

---

### Post by coffeecat on 2009-04-26
**Edit:**   Sorry - posted in error. Didn't see the reference to RAID.

---

