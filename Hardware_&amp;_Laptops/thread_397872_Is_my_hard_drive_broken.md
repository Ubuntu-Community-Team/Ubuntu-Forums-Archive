---
title: "Is my hard drive broken"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by tictacman on 2007-03-31
All of a sudden every time I load up fsck interrupts the splash with stuff like this:

ReiserFS: sda4: found reiserfs format "3.6" with standard journal
Mar 31 15:00:32 lounge kernel: [17179643.876000] ReiserFS: sda4: using ordered data mode
Mar 31 15:00:32 lounge kernel: [17179643.896000] ReiserFS: sda4: journal params: device sda4, size 8192, journal first block $
Mar 31 15:00:32 lounge kernel: [17179643.896000] ReiserFS: sda4: checking transaction log (sda4)
Mar 31 15:00:32 lounge kernel: [17179643.908000] ReiserFS: sda4: Using r5 hash to sort names
Mar 31 15:00:32 lounge kernel: [17179643.932000] kjournald starting.  Commit interval 5 seconds

In fstab my root partition has an entry like this:

# /dev/sda1
UUID=6f8666fe-75aa-43e4-8912-5c11fc0c7205 /               ext3    defaults,errors=remount-ro 0       1


I can't ever remember seeing errors=remount-ro before so I'm not sure what's happening here.

---

### Post by benerivo on 2007-03-31
It doesn't look like the splash message reports any errors with the drive, but you may want to alter the fstab so that it doesn't bother checking it during boot. I think a change to...
# /dev/sda1
 UUID=6f8666fe-75aa-43e4-8912-5c11fc0c7205 / ext3 defaults,ro 0 0
would skip the checking sequence, although there is always the possibility the booting may fail. I'm no expert.

---

