---
title: "[SOLVED] PLEASE help: accidentally deleted linux partition through windows install ma"
date: 2008-10-18
forum: General Help
---

### Post by conphuzed on 2008-10-18
_problem:_ i think i deleted my linux partition (but i did NOT reformat it)
[U]
question:[/U] can i recover the linux install, since i have only deleted the partition and NOT reformated it?

_details:_ previously i had dual boot setup with ubuntu + XP, each on their own partition obviously, but i wasn't sure which partition each was on. i wanted to reinstall the windows one so i deleted the partition i thought windows was on. apparently i deleted the linux partition because now when i try to boot, grub doesn't appear and the message 'no operating system found' or something to that effect appears.

_fdisk:_

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x381ff000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19574   157228123+   7  HPFS/NTFS
/dev/sda2           19575       30401    86967877+   5  Extended
/dev/sda5           19575       29955    83385351   83  Linux
/dev/sda6           29956       30401     3582463+  82  Linux swap / Solaris
```

the first partition (sda1) is the one i deleted. the fdisk above appears exactly the same as it did before i deleted that partition, so i don't really understand what happened. linux still appears on sda5, but why can't i boot it?

---

### Post by Sam on 2008-10-18
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by PocketDog on 2008-10-18
I've done exactly the same thing a while ago. I burnt Acronis Disk Director Suite to a (bootable) CD and it found and undeleted my lost partitions with no trouble at all

---

### Post by conphuzed on 2008-10-18
i tried the 'rescue START END' method in parted, but it doesn't seem to do anything (it just brings the prompt '(parted)' up again)

i believe the linux partitions are still in tact, i think what may have happened is the windows installer rewrote my grub menu or my partition table or something so no partitions appear, rather than just removing the partition i deleted. any ideas?

edit:

[COLOR="Red"]SOLVED:[/COLOR] i have recovered everything by restoring grub. i'm gonna try and reinstall windows without messing this up again now

thanks for all your help guys, much appreciated as always

---

