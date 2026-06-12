---
title: "Findig a hard drive in Ddrescue"
date: 2014-01-10
forum: Hardware
---

### Post by shadowfire452 on 2014-01-10
So, I have a 2.5" Western Digital SATA hard drive from a laptop. I suspect the firmware to be bad, as the laptop doesn't recognize a boot device with it in. I've taken the hard drive out and put it in a linux computer, and I'm trying to clone it. I can feel the drive spin up, and it only clicks every once in a while. I've gone though the disk utility, used lshw -c disk -short, and cat /proc/partitions and I can't find it in there. Also, I'm not very experienced with linux, but I noticed I have an 80Gb HDD on dm-0 while I only have 1 80 Gb disk in my computer thats on sda, so I'm not sure what that is.

---

### Post by houstonbofh on 2014-01-11
Hard drives can fail for many reasons.  It can be the magnetic media, the drive motor, the seek motor, or the control board.  The only one ddrescue can fix is the magnetic media...  The click of death is usually a bad drive motor or control board.  You can try sticking it in a freezer and seeing how much data you can pull before it warms up, but you are mostly out of luck.

---

