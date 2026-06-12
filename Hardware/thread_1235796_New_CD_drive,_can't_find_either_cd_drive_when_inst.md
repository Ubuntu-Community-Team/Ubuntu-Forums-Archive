---
title: "New CD drive, can't find either cd drive when installed."
date: 2009-08-09
forum: Hardware
---

### Post by Xavier Oddmon on 2009-08-09
Hello! I have a dell dimension 8300 desktop, with two CD drives. The bottom drive is a burner, the top one is not. The CD burner recently crapped out. So I bought an i/o Magic DVD + R/RW burner with light scribe. However, when this drive is installed, neither the top nor bottom drive are useable, and niether of them show up in /dev/. The machine is dual boot, and the drives don't show up in windows either. Removing the new drive, and placing the old CD drive in the slot makes them both appear again. Physically, there is one ribbon cable, which splits into one black connector (top) and one white connector (bottom.) There is also one power cable which splits. When the drives are not working, they still light up upon booting, and eject when I press the face button. What's going on? Is the new drive dead, or is there more likely something wrong on my end?

---

### Post by jerrrys on 2009-08-09
something to check would be the pinout on the back of the new drive.  should it be set to master or slave.

---

### Post by lisati on 2009-08-09
> **jerrrys said:**
> something to check would be the pinout on the back of the new drive.  should it be set to master or slave.

... or possibly "Cable select"

---

### Post by khelben1979 on 2009-08-09
I seriously think that you would benefit from replacing that new CD drive with a more well known brand, it doesn't need to be expensive.

If you still insists on making it work without replacing it, you could post some pictures on how the cables are sitting. Is it [S-ATA]("http://en.wikipedia.org/wiki/S-ATA") or [P-ATA]("http://en.wikipedia.org/wiki/P-ATA") cables? Have you looked in BIOS to see if it manages to find the drive?

---

### Post by jerrrys on 2009-08-09
although not your exact drive, you may find this helpful

[http://reviews.cnet.com/4520-6603_7-5118840-1.html](http://reviews.cnet.com/4520-6603_7-5118840-1.html)

---

### Post by Xavier Oddmon on 2009-08-10
It's ATA, set to slave.. The master drive (old) is connected to the master connector, on top, and the slave drive (new) is connected to the slave connector in the middle of the cable. 


However! After spending an afternoon on this, and scouring the internet, I took it back to staples, and got an external. Problem solved. Or rather, averted.

PS. I have reason to believe that the problem is not the new drive, but rather something internal. The original burner has been replaced twice, and is doing weird things (making strange noises, it'll stop burning half way through a disk, or even report that it is burning very quickly. The disks that result are not blank, but not usable either.) Strangely, it can read disks just fine, and so did the previous ones. (not the same disk drive/manufacturer)

---

