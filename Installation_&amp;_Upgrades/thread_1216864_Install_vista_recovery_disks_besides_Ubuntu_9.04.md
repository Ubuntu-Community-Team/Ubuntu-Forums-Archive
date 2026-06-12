---
title: "Install vista recovery disks besides Ubuntu 9.04"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by joy83 on 2009-07-18
My Gateway desktop came with Vista 64 bit on its 500gb drive. It also has 2 separate hard drive bays for extra hard drives. I put one of my old 160gb hard drives from my old desktop in one of them.

Now after I bought the computer I installed Ubuntu 9.04 entirely on my 500gb hard drive thus erasing my Vista installation(I made recovery disks though before I did that :p). What I now want is to install Vista on my 160gb drive that I put.

I put the recovery disk and restart the machine but it seems like it wants to install Vista and go back to factory settings on the 500gb hard drive thus erasing Ubuntu in the process which I don't want, it also doesn't give me any options on selecting hard drives.

Any suggestions on how I install Vista and get factory settings back on my 150gb hard drive and still keep my 500gb Ubuntu drive.

The other problem is I cannot swap the drives without opening the case. I could put the 160gb drive without opening the case since it has a hard drive bay accessible from the front.

---

### Post by Mark Phelps on 2009-07-18
The recovery disks are most probably trying to reinstall Vista on the first hard drive they find -- the original drive. You'll have to change your boot options to have the disk you want to install to as the first drive.  If that's not possible, you'll have to open the case and unplug the old drive, and pluging the new drive (for Vista).

---

### Post by snakeman21 on 2009-07-18
Hehe, unfortunately, Microsoft doesn't seem to like the idea of installing to anything besides the first hard disk.  The only way to do it is to open the computer, remove the 500GB drive, close the case, install Windows to the hard drive of your choice, open up the case again, put your 500GB drive back, and close up the case.

---

### Post by Sef on 2009-07-18
Windows needs to be on the first primary partition, so you may want to make the 160 your master and the 500 your slave.

---

