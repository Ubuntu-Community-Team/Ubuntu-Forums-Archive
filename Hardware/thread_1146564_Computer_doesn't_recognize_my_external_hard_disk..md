---
title: "Computer doesn't recognize my external hard disk."
date: 2009-05-02
forum: Hardware
---

### Post by sapple on 2009-05-02
Hello,

I have an external harddisk which I can connect to the computer with USB. However when I plug it in, my computer (running Xubuntu 8.04) doesn't recognize it. Nothing happens.

I try plugging in a flash disk, it is ok, it is recognized properly. I also try this external harddisk on different computers (both running XP or Ubuntu), and it works fine there also. It only doesnt work on my computer.

What should I do ?

Note: I type fdisk -l and here is the output:

Disk /dev/sda: 20.4 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13651364

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2421    19446651   83  Linux
/dev/sda2            2422        2490      554242+   5  Extended
/dev/sda5            2422        2490      554211   82  Linux swap / Solaris


So it doesnt recognize it. (my external HD is 100GB and has 3 partitions)

---

