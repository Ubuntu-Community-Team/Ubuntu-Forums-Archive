---
title: "Partition Problems"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by amtur_poet on 2007-11-23
I tried to install ubuntu 7.10 from the live CD, and I partitioned 60gb of my hard drive, but that got an error, and now I have about 3/4 my hard drive locked out as unallocated free space. I tried to re-allocate it with paragon partition editor, but nothing happened. Does anyone have any ideas on how to fix this?

---

### Post by bingoUV on 2007-11-24
1. What error did you get when you tried to partition 60gb of hard drive through ubuntu installer?

2. What happens if you try to install ubuntu again?

3. Boot into live CD, open a terminal (Applications -> System Tools -> Terminal) and paste this. Give the output here.
```

sudo /sbin/fdisk -l

```

---

### Post by amtur_poet on 2007-11-24
> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11f14a84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1217        9203    64147461    7  HPFS/NTFS
 That was the output.

There actually was no error message; the disk resizing bar was just stuck at 0% for a day or so, so I decided to close it.

I tried to install ubuntu again, but it just made the unallocated space bigger.

---

### Post by amtur_poet on 2007-11-25
Can someone please help me? I'm sorry I double-posted, but I really need to get that free space back to my windows partition.

---

### Post by AlanRogers on 2007-11-26
As mentioned on your other thread, GParted can be run from a Live CD and should be capable of extending your small partition to fill the remainder of the disk or create another partition there. You can [get it here]("http://gparted-livecd.tuxfamily.org/") and I've successfully used it on Windows and Linux machines. Be carefully with NTFS though; defrag thoroughly first.

---

