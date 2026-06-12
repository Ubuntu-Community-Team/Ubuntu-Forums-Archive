---
title: "[SOLVED] porn locked away in ntfs external hard drive"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by Zerocool10482 on 2007-12-04
Hi, I have an external hard drive that formated in ntfs and I've tried ntfs config tool. Didn't work. but I can see my xp partition. I wanted to back up everything to the ntfs because of work reasons. I just need to read/write to it. In the last version of Ubuntu it just picked up the drirve but now it doesn't what up with that?

Anyway can someone please help. I need my porn. NO ******* joke. Porn is locked away and i need to play. I know I can google for more but it's the classics I want.

Thanks again

---

### Post by Friek on 2007-12-06
It's hard to tell without additional details. Did you try mounting it anyway? ;)
Does it still work in XP?

Why didn't you use vfat (FAT32 in windoze terms) anyway. Writing to NTFS partitions from linux is still a bad idea, as the write support is still highly experimental.

---

### Post by Sutur on 2007-12-06
Man, gotta admire your honesty...

I doubt this helps because you probably already know but if you insist on keeping your backup using the NTFS format, do you definitely have **ntfs-3g** installed?

---

### Post by Zerocool10482 on 2007-12-07
I have ntfs-3g installed and I had to do this for work. But for got about fat32. But is there anything else I can use? like a command line I could use?

---

### Post by Zerocool10482 on 2007-12-07
I found out how to get it working. Theres some 3rd party software with maxtor I had to install on windows to open it up.

---

### Post by victorgreen on 2007-12-07
uh ive had ntfs read write working for me since edgy. All 4 of my external drives are ntfs, Ive got ntfs data share partitions on my main drives, Gutsy has read write support out of box and it works great.

---

