---
title: "Sata raid questions"
date: 2008-07-14
forum: Hardware
---

### Post by dirtmaster88 on 2008-07-14
Hello All,

I am currently on vista at the moment with two 500gb drives in raid 0. I would like to fully switch over to ubuntu with possibly a dual boot. The reason i'm posting this thread is because I also have a sata dvd burner. It took me weeks to figure out the correct setup in windows to make my sata raid work with my sata burner.

Am I going to have any issues with ubuntu having a sata raid and a sata dvd burner?

My Hardware Specs:
EVGA 780i motherboard
Core 2 Duo E8400
4gb Crucial Ballistix Ram
EVGA 9800GTX pci-e 2.0 vid card
PC P&C 750w Power Supply
**2x - Seagate 7200.11 500gb SATA drives**
**Asus SATA 20x DVD burner**

---

### Post by Victormd on 2008-07-14
Chances are Yes, you'll have to struggle a bit to get it working. Backup all your data before attempting and be aware that you might need to re-install windows. What RAID controller do you have? Is it an on-board controller? Ubuntu (linux in general) prefers off-board controllers and you might have some issues with this as well because they are software controlled (through your BIOS) and not hardware controlled (as the off-board controllers).

---

