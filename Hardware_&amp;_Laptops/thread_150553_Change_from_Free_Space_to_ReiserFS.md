---
title: "Change from Free Space to ReiserFS"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by lullebakman on 2006-03-26
I was trying to install Mac OS X on my x86 PC with VMware. The install part didn't work. I rebooted after a while. And there was a GRUB error, I think it was error 17 or 20.

No problem, I removed GRUB in the Rescue Mode. I wanted to reinstall it but my WLAN card doesn't work in the Rescue Mode, so I couldn't reinstall it.
 
For the 2nd time: no problem (I thought) I wanted to boot into Windows (I had a dual boot config) but there was an error:
```

A disk read error occured

Press CTRL+ALT+DEL to restart
``` I searched for a solution and tried to rebuild my partition table and my MBR.
I did, but nothing changed. CHKDSK didn't work. The Partition Magic Rescue floppies told me that my C partition had this problem: "Bad Signature ERROR 1507"

So I decided to reinstall Windows XP. I hoped all my data on another NTFS partition would be saved and it was!

This was just a little introduction. Now the real problem:
I had a third partition formatted in ReiserFS with Breezy on. The partion table rebuilder didn't know ReiserFS so the Breezy Partition is now indicated as freespace.

So what I would like to know:
**How do you change a partition indicated as freespace to ReiserFS?**

I tried it with PTEDIT from PowerQuest, but it didn't know ReiserFS.

---

### Post by lullebakman on 2006-03-27
Nobody?

I'm just searching for a tool that can change the type of partition
ex.: 07 for NTFS, 83 for ext2 & 3 and reiserfs, 82 for Swap Partition.
I need it to change a partition from 00 (free space) to 83 (reiserfs)

---

