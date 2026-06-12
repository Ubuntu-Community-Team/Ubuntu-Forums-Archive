---
title: "gParted Messed with external USB drive"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by Arithmomaniac on 2007-08-13
I used to be be an active Dapper user, but right now I just use it as a LiveCD. 

I had a new external hard drive I wanted to use in Windows XP (ioni 40 GB), but first I wanted to make a 5 GB partition to put PuppyLinux or Ubuntu on. I decided the best way to do this would be through G-Parted, included on Dapper when running a LiveCD.

I booted it up, and sure enough, a blank FAT32 hard drive appeared as media/sda1 (if memory serves), with a lock icon "boot" tag on it. Now, I knew that was baloney (I didn't boot of of it), so I unmounted it and created a 5GB Fat32 Partition and a 35GB NTFS partition.

I tell it to run. It creates the first partition properly, but then Nautilus pops up showing the drive, and at the same time, an error message occurs, and I have to start over.

Now this time, the Fat32 Drive just shows up as an unknown file type with a lock. I try to turn it into Fat32. Again, Nautilus pops up and it is ruined.

Now, I just delete all partitions, leaving an "unknown" partition with a lock. Despi te the fact tha I hae been running in Sudo the whole time, it still won't make a Fat32 partition.

I go back to Windows. the Fat32 drive is now 5 GB.

I go back to Ubuntu. No formatting at all.

I'd just use the Ultimate Boot CD and play around, but it's a USB device, and I don't know if it will be recognized...

What happened, what mistakes did I make, and how would I fix them?

---

### Post by Arithmomaniac on 2007-08-13
bump

---

