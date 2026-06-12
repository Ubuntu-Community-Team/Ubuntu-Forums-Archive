---
title: "problem with partition table or drive ?"
date: 2008-10-22
forum: Hardware
---

### Post by usman idrees on 2008-10-22
hi
last night i tried to change my drive names so i dont know what happened,now i can not see my data ???hheheh ...so in the morning the computer started with no booting ? i tried to fix it with fsck and gave this command : fsck /dev/sda1 and sda2 , the message was
the file system size (according to super block) is 4883752
the physical size of the device is 4646793 blocks.either the superblock or the partitiontable is likely to be corrupt
so then i tried testdisk to fix this but invain ??? can any body help me ??
thanks in advance

---

### Post by didac on 2008-10-23
Boot from the LiveCD, unmount /dev/sda1 and /dev/sda2 if they're mounted and run sudo e2fsck -p

Then cross your fingers and pray for the best.

---

