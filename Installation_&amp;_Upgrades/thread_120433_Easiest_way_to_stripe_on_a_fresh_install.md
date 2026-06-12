---
title: "Easiest way to stripe on a fresh install?"
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by jtrask on 2006-01-21
Alright, I'll try this again. I have two SATA 120gb's that I'd like to set up with the performance boost of striping. I don't particularly care how it's done (my mobo does have onboard RAID, but I hear LVM can stripe as well) as I don't have existing data, don't want a dual-boot with Windows, and don't know much about Linux partitioning in the first place (including anything about LVM etc...) What's the easiest way for me to do a clean installation of Ubuntu on my new amd64 system and stripe these hard drives?

---

### Post by Ocxic on 2006-01-21
install ubuntu to one of your hardisk like normal and then follow this guide, prolly the easiest way:
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html)
that will make your 2 hard drives into one partiton and give you the space you want, I'm doin this once dapper drake is released.
after reading through the guid it may not be exactly what you want, tho it may be easier to do this then to install to a direct raid setup.

---

### Post by jtrask on 2006-01-21
If I do it that way, when I get to the partitioning step of the installation on the first disk, do I want to use LVM or not?

---

