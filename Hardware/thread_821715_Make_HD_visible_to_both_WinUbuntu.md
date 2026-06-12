---
title: "Make HD visible to both Win/Ubuntu"
date: 2008-06-07
forum: Hardware
---

### Post by mparker81 on 2008-06-07
i replaced my desktop with a large laptop about a year ago and i recently dual boot with ubuntu...   i use ubuntu and my wife still likes windows...  and to be honest, there are still somethings i find easier to do in windows as of now. but my problem is, how do i make files accessible to both OS's. 

i have the ability to add anouther hard drive to my laptop (HP dv9000) ive been thinking about getting a 320gig...  but id like to be able to access the info on it with both systems. 

is this possible?

thanks guys

---

### Post by thideras on 2008-06-07
You could format it a few ways:

FAT32 - Easiest, both can read/write to it no problem.  File size limitation of 4Gib
NTFS - Easy for Windows, linux will need ntfs-3g and mount as readable.
EXT3 - Easy for linux, Windows will need a program to read from it, not sure about writing

I would suggest FAT32 if you are not going to have files over 4Gib each.

---

### Post by mparker81 on 2008-06-07
thanks for the fast reply...

i checked package manager and searched for ntfs-3g and it had it listed as already being installed...  so how do i locate my documents in windows from ubuntu?

---

### Post by thideras on 2008-06-07
> **mparker81 said:**
> thanks for the fast reply...

i checked package manager and searched for ntfs-3g and it had it listed as already being installed...  so how do i locate my documents in windows from ubuntu?You will have to mount the drive first.

Here are instructions:

[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot)

---

