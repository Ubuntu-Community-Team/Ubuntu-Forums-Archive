---
title: "Possible reason for gparted crash."
date: 2008-07-13
forum: General Help
---

### Post by mempman on 2008-07-13
I was moving a approximately 25 gigs of free space about a partition.  When the process was almost done, my laptop completely shutdown all of a sudden.  Since, I had to reinstall but I am very curious to know why is it that the computer shutdown all of a sudden.

Could it be because maybe the cpu overheated and as a security feature the bios forced a system shutdown?  Could there be other reasons?  Any ideas?

---

### Post by carlinuxlearner on 2008-07-13
It is most likely that your CPU over heated, because that's always a one of the symptoms.

C@RL

---

### Post by VMC on 2008-07-13
The reason could be any number of things. When you say you were moving 25gb of free space. Exactly how did you move it? What partition, root, /home, or something else.

---

### Post by BLTicklemonster on 2008-07-13
I found out a little while ago that if you have a spare hard drive you want to partition, don't make it a primary. 

I'm still trying to figure out how to get the machine going. Got ultimate boot cd in on it right now formatting the drives. Ubuntu nutted up every time I tried on either drive, together or one at a time.

Sheesh.

---

### Post by mempman on 2008-07-14
> **VMC said:**
> The reason could be any number of things. When you say you were moving 25gb of free space. Exactly how did you move it? What partition, root, /home, or something else.


Well I had 25 gigs following my / partition and I wanted to move it such that my root partition was after the freespace.

---

### Post by cariboo on 2008-07-14
To BLTicklemonster there must be something not right with your setup because I've got 4 hdd's installed and only one drive has an extended partion, all the rest are primaries.

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066acc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825       20023   146183467+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5948d181

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45aaf2bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS
/dev/sdc2            9729       19457    78148192+  83  Linux

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51b6cc16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       10199    81920000    7  HPFS/NTFS
/dev/sdd3           10200       30401   162272565    5  Extended
/dev/sdd5           29697       30401     5662881   82  Linux swap / Solaris
/dev/sdd6           10200       11050     6835594+  83  Linux
/dev/sdd7           11051       29696   149773963+  83  Linux

```

Jim

---

### Post by BLTicklemonster on 2008-07-14
Then perhaps the drive went overboard?

I'm running everything I can on it right now to see if I can fix it.

Maxblast is the last thing I'm doing, but each time I reboot, I'm told that the drive is operating outside it's parameters or something like that.

---

### Post by VMC on 2008-07-14
> **mempman said:**
> Well I had 25 gigs following my / partition and I wanted to move it such that my root partition was after the freespace.

I wonder if something got moved that was vidal at the time of the move. What process did you use to move part of the partition, gparted?

---

### Post by mempman on 2008-07-15
> **VMC said:**
> I wonder if something got moved that was vidal at the time of the move. What process did you use to move part of the partition, gparted?

I don't think this is a possibility as I was running gparted live cd.  I really think it must have been the overheating possibility?? what u think?

---

