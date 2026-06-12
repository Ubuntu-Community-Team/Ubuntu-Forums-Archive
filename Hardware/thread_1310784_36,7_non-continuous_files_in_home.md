---
title: "36,7 non-continuous files in /home/"
date: 2009-11-02
forum: Hardware
---

### Post by dumas33 on 2009-11-02
Few months ago I realised that my system boots up slow. In our office we have 3 similar dell latitude laptops running ubuntu 9.04 (now 9.10) and mine is booting about 25 second slower. 
I hoped, that upgrading to karmic will solve the problem, but it did not. After routine checking of drive in report was written that home partition has 36,7 non-continuous files. Even for NTFS it's a lot, not to mention fragmentation resistant ext4. I'm guessing, that cause of this fragmentation was shrinking of that partition by 40 Gb. Later I resized this partition to former state, but seems that fragmentation left.

I think fragmentation is the main reason of slow booting. How to de-fragment his partition?

Additional info: Partition has 45% of free space (89Gb), it is ext4.

Any suggestions?

---

