---
title: "Bad sectors"
date: 2010-09-26
forum: Hardware
---

### Post by Gamerboy on 2010-09-26
Is there any way to Remap or repair bad sectors in ubuntu 10.04 ?  
Why does this happen actually?

---

### Post by PresenceofMind on 2010-09-26
> Is there any way to Remap or repair bad sectors in ubuntu 10.04 ? 

Bad Sectors are permanent faults......u can't remove a bad sector from a drive platter. The OS would normally mark those bits as 'unusable' and skip these sectors. Newer Hard Disk Drives can remap data onto a different part of the drive automatically when the disk controller detects it......

> Why does this happen actually?

Physical damage to the platter (i.e. the shiny discs).

---

### Post by efflandt on 2010-09-26
See **man e2fsck** about how to handle badblocks for ext2/ext3/ext4.  Not sure what options are best, but maybe -ccfk.  You cannot do that on a mounted file system and it is probably best to do that on an empty file system before you put anything on that partition.  You would have to prefix the command with **sudo** and it can take a very long time.  I think one time a 60 GB disk had so many badblocks, I gave up after 11 hours.

As mentioned virtually any current hard drive reserves space to map good sectors in place of bad sectors automatically and transparently.  If you start actually seeing bad sectors that is a bad sign that all the error sectors are used up and the drive will likely deteriorate further.  So you should back up whatever data not already save and replace the drive before it corrupts the file system and partition table.

The platters spin very rapidly and the heads float on a very thin cushion of air, so it does not take much of a bump with the drive running for a head to contact the platter and scrape off some magnetic material.  And once you get loose material bouncing around on those fast spinning platters things can only get worse.  So you should be very care bumping into or moving a computer or laptop that is running (unless it has a solid state flash drive).  A hard drive can take more abuse when it is off because the heads are parked away from the platters.  But you can still break something if it is dropped onto a hard floor.

---

