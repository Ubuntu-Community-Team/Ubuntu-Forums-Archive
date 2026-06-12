---
title: "Gparted problem"
date: 2008-09-07
forum: General Help
---

### Post by boyce1 on 2008-09-07
I had this problem a while ago, but have only realised that i now need to change my partitions.

when i scan my hdd with gparted livecd, it comes up with everything as an unallocated space, all 250gb of it. also from gparted in gutsy, still nothing.

[B]
however i notice this[/B]

jack@jack:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 30401.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
omitting empty partition (5)

Command (m for help): 


I don't know how to fix this, but according to gutsy it isn't a problem.


fdisk-l seems to be ok?

jack@jack:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13581357

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       30401   192996877+   5  Extended
/dev/sda3           29646       30401     6072538+  82  Linux swap / Solaris
/dev/sda5            6375       28888   180843642   83  Linux
/dev/sda6           28889       29645     6080571   82  Linux swap / Solaris


any help would be greatly appreciated

---

### Post by Shazaam on 2008-09-07
STOP! Press Q to quit fdisk. I hope you didn't make any changes. Cold boot (from complete system shutdown) the gparted livecd. When it gets you to the first screen choose the one labeled "VESA". See if it makes any difference when it is done scanning your disks.

---

### Post by boyce1 on 2008-09-07
Could it not have anything to do with me having 2 swaps? i think one was left over after i did a clean install of hardy, so the gutsy swap is still there...

---

### Post by boyce1 on 2008-09-07
ive also noticed, that fdisk -l says the swaps are sda 3 and 6, whilst fstab says the swaps are sda 5 and 7...

---

### Post by Shazaam on 2008-09-07
The reason I gave you those instructions is because gparted does that sometimes (unallocated space reading). I had that happen to me so I panicked and ran testdisk totally trashing Windows and 3 other os's. After a rebuild I later had it happen again and a simple reboot of the gparted cd made the partitions "magically" reappear.

---

### Post by boyce1 on 2008-09-07
i tried the VESA option, didn't work either.

---

### Post by boyce1 on 2008-09-08
:(

---

### Post by Rorke on 2008-09-10
I have exactly this problem. I had a power failure whilst moving and shrinking my main partition. I put in the XP CD and formatted the first partition. Then Live CD wouldn't see any partition. I booted from Super Grub Boot and got my Ubunto back, but now ITS Gparted sees the whole disk as unallocated!

simon@simon:~$ sudo fdisk -l
[sudo] password for simon: 
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000deca2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3230    25944943+   7  HPFS/NTFS
/dev/sda2            3231       30401   218251057+   5  Extended
/dev/sda3           29646       30401     6072538+  82  Linux swap / Solaris
/dev/sda5           10826       28888   145091016   83  Linux
/dev/sda6           28889       29645     6080571   82  Linux swap / Solaris
simon@simon:~$

---

