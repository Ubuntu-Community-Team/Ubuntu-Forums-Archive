---
title: "Multiple, unmatched harddrives with a dual boot"
date: 2008-11-22
forum: General Help
---

### Post by invisibled on 2008-11-22
OK, I've done a bit of searching and I couldn't find direct answers to what I'm looking to do. So, here we go ...

I currently have a 120 gb harddrive, and I'm going to get another, higher capacity harddrive. I want to run a dual-boot with XP and Ubuntu. My questions being, would grub still work if I had a 120 gb drive, and (for example) a 500 gb drive? Ideally, I'd like XP to be on the smaller drive, and Ubuntu to be on the larger drive.

---

### Post by cariboo on 2008-11-22
Grub has nothing to do with disk capacity, You can have as many different size hard drives as you got connectors for. Linux deals with large capaicty hard drives much better than an ancient OS like windows XP :). 

In my server for example, I boot from a 120Gb IDE drive, I have a 80Gb IDE drive for backups and have a 400Gb SATA raid 1 array.

Jim

---

### Post by Skripka on 2008-11-22
> **invisibled said:**
> OK, I've done a bit of searching and I couldn't find direct answers to what I'm looking to do. So, here we go ...

I currently have a 120 gb harddrive, and I'm going to get another, higher capacity harddrive. I want to run a dual-boot with XP and Ubuntu. My questions being, would grub still work if I had a 120 gb drive, and (for example) a 500 gb drive? Ideally, I'd like XP to be on the smaller drive, and Ubuntu to be on the larger drive.

I'd consider reversing that if I were you, unless you have that many media files/documents (mp3 etc etc)..  Windows apps and OSes take up MUCH more space than linux ones do.

---

### Post by caljohnsmith on 2008-11-23
> **cariboo907 said:**
> Grub has nothing to do with disk capacity.
Unfortunately, that is not true in some cases; disk capacity does matter to Grub sometimes. :) Some older BIOSes cannot access anything on a HDD past 137 GB (see [this article]("http://en.wikipedia.org/wiki/Advanced_Technology_Attachment") for more details). If that's the case, then it is important to put both Grub and Ubuntu's boot files inside that 137 GB limit or you won't be able to boot Ubuntu. Hopefully invisibled doesn't have that BIOS limitation and won't have to worry about it.

---

### Post by invisibled on 2008-11-30
I have a new'ish motherboard (> 3 years-old) and so I don't expect it to be a problem. Anyway, thanks for all the help guys. These boards and everyone on 'em are amazing.

---

