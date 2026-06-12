---
title: "partman shows nothing??"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by Loser777 on 2009-04-09
Trying to install 8.10 on a system here, but when it gets to the partman part of the install, there are no partitions or volumes in the table. All of the options to modify or create partitions are also greyed out... The drive I'm attempting to reformat and install on is a 640GB SATA II (Currently formatted as NTFS)
I know the drive is fine because Windows will boot fine and it is detected by BIOS just fine.
Causes?Fixes?

---

### Post by ronparent on 2009-04-09
I have been warning people that such an appearence indicates that they are probably dealing with two drives in a raid0 array. You can verify this by opening a terminal after booting to your live cd and running 'sudo sfdisk -l'. If you do have two drives the output from this command will show them. Unless we can confirm otherwise, do not attempt an install from that disk. Only an alternative cd can deal with a raid array!

---

### Post by Loser777 on 2009-04-09
I'm 100% sure that I do not have a RAID array. After building this PC in June '08, I've never even partitioned the hard drive, much less created a raid array.

I just burned a 9.04 CD to see if that would help... now I'm getting the "Exit Code 10" from partman.

---

### Post by ronparent on 2009-04-09
Good enough for me. Are you running vista? How many primary partitions do you have? Try postint he output from 'susd sfdisk -i'.

---

### Post by Loser777 on 2009-04-09
No, XP 64-bit SP2.
Just 1 Primary partion; NTFS.
Output from sudo sdfisk -l:
   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  77823   77824- 625121248+   7  HPFS/NTFS
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

---

