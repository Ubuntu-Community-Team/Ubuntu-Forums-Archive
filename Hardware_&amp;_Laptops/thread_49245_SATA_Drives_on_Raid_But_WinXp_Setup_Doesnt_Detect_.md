---
title: "SATA Drives on Raid But WinXp Setup Doesnt Detect the raid."
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by Trainee1 on 2005-07-15
Hey, I have a lil problem...I have 2 80gb Maxtor sata harddrives and they are on stripping raid, i have everything setup in the bios correctly (i think) but when i try to install windows i get to the part where it shows my harddrives but it shows them both separate when its suppose to detect it as one big harddrive cause of the raid. I must be missing somthing so if you guys know how to fix it then that would be great.

My Motherboard is...

MSI K8N Neo2 Platinum w/ Orginal bios version it came with.

---

### Post by OzPhoenix on 2005-07-18
I've got almost the exact same scenario. Did you ever figure out how to get this to work?

I've got two 80GB SATA drives hooked into an ABIT AN7 mobo. I've created a RAID set (Type 1 for mirrored - so slightly different) but ubuntu install just reports two scsi drives.

Please help,
OP.

---

### Post by pressureman on 2005-07-18
[QUOTE=OzPhoenix]I've got two 80GB SATA drives hooked into an ABIT AN7 mobo. I've created a RAID set (Type 1 for mirrored - so slightly different) but ubuntu install just reports two scsi drives.[/QUOTE]

Many cheap motherboard SATA RAID controllers are based on Silicon Image 3112(a) chipsets, which Linux supports, but not as a RAID controller. It will simply see multiple /dev/sd? devices, which you can then use Linux software RAID on (in many cases, faster for RAID0 or RAID1).

As for the previous post about Windows (remembering this is an Ubuntu forum), I suspect that the controller is set to compatibility mode (emulates PATA), and the correct Windows fakeraid driver hasn't been installed.

---

### Post by OzPhoenix on 2005-07-18
[QUOTE=pressureman]Many cheap motherboard SATA RAID controllers are based on Silicon Image 3112(a) chipsets, which Linux supports, but not as a RAID controller. It will simply see multiple /dev/sd? devices, which you can then use Linux software RAID on (in many cases, faster for RAID0 or RAID1).[/QUOTE]

Cheers dude, that clarifies it all for me. I read something else about these chips being hybrid (software/hardware) and from what you've just said it's yet another confirmation - as that's the chip my mobo has.

That's kinda annoying see I purchased that mobo for that feature, but anyway, I'll go software then.

Cheers,
OP.

---

### Post by Trainee1 on 2005-07-20
yeah i fixed my problem, all i had to do was reset the bios jumpers on the motherboard

---

### Post by OzPhoenix on 2005-07-20
Oh, just noticed something. Was this post specific to the windows install and thereby nothing to do with Ubuntu? As it's the Ubuntu installer I'm having this issue with.

hmmm... guess I'll look for some jumpers anyway....

---

### Post by RoadRunner_UK on 2008-03-17
Did anyone ever resolve this?

I have an Abit AN7 mobo with a RAID01 array which Ubuntu sees as 4 individual drives, but windows sees as a single array.

What I'm Tryin To Do:
I have 4x400gb SATAII drives which I'd like to use as a RAID0 array with tolerance.
My MoBo SATA controller suports 2 sets of 2 drives in a mirror, so I get 800g of space, with RAID0 speed and RAID1 tollerance.

On this single 'drive' I'd like 2 partitions, 1 for Windows, 1 for Ubuntu.

I'd like to choose between installs using GRUB at boot.


Now, i dont mind setting the array up in Ubuntu, just so long as I can have a bootable XP partition.

Any ideas?

---

### Post by nutz on 2008-03-18
Same issue here, Ubuntu sees the two drives as being separate. Is this just a driver issue?

---

