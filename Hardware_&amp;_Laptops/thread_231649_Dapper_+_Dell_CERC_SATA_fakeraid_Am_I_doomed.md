---
title: "Dapper + Dell CERC SATA fakeraid: Am I doomed?"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by glowingpear on 2006-08-07
Hey all,

I've done a lot of research on this issue, and from what I can tell, I might be out of luck.  I wanted to post a last-ditch plea for help in case someone had miraculously gotten this hardware to play nice with Ubuntu.

The Dell Precision 470 in question is already running WinXP on a RAID 0 array of two disks and I'd like to dual-boot.  When I boot off the Dapper LiveCD, though, GPartEd sees sda and sdb separately.  Googling and forum-searching led me to a driver called aacraid, which was apparently removed from the kernel in recent releases...?  I already tried the latest version of dmraid with no luck--it said "no RAID disks found."

Any advice?

---

### Post by glowingpear on 2006-08-07
Update: even though aacraid won't load by default, I was able to load it manually.  GPartEd is still clueless, but fdisk can see the Dell utility partition and the big 155GB NTFS partition.

Any ideas as to how I can go from here to resizing the NTFS partition and setting up a dual-boot using GRUB?  Preferably without thrashing Windows? :)

---

