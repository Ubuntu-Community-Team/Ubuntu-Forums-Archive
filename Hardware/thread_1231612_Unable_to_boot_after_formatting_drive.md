---
title: "Unable to boot after formatting drive"
date: 2009-08-04
forum: Hardware
---

### Post by Cal27 on 2009-08-04
A couple days ago, I blanked a 250 GB hard drive that I had been using as storage with dd. After it was done, I used gparted to partition it and add a file system. It seemed to work fine, but after I rebooted, my computer hung on "Verifying DMI Pool Data." If I remove the disk however, my computer boots with no problem. When booting from the live CD, Ubuntu recognizes the disk and there doesn't seem to be anything particularly wrong with the disk.

Sometimes my computer will get past Verifying DMI Pool Data (or maybe it times out) and try to run nVidia Boot Agent, but that fails. After that it tries Pre-Booot eXecution Environment and that fails too, so it asks for a system disk. (I'm not sure if both of those run and I just don't see them or if they're some sort of backup method).
I'm completely stumped as to what the problem could be, any help would be greatly appreciated.

---

### Post by Cal27 on 2009-08-06
Bah, now it won't boot from anything except the live CD. I'm starting to consider the possibility of this being a coincidence and it's completely unrelated to my hard drive...

---

### Post by Cal27 on 2009-08-07
bump

---

### Post by Cal27 on 2009-08-07
bamp

---

### Post by hansdown on 2009-08-07
Hi Cal27.

I may not be able to solve this, but I'd like to help bump your thread and
offer some help.

I found some info to help you diagnose the problem.

[http://www.computerhope.com/issues/ch000474.htm](http://www.computerhope.com/issues/ch000474.htm)

[http://www.duxcw.com/faq/computer/dmi.html](http://www.duxcw.com/faq/computer/dmi.html)

---

### Post by Cal27 on 2009-08-07
Thanks handsdown, I've tried some of the diagnoses from those sites and I'm thinking that it might be either:
I don't have a floppy drive connected and that's causing problems (although it never did before)
or the boot info on my drive is corrupt in some way.

Is there a command I can use to verify my boot information?

---

### Post by Cal27 on 2009-08-07
Oh, and here's exactly what happens when I try to boot:
```

Verifying DMI Pool Data . . . . . . .
Boot from CD :
Boot from CD :

NVIDIA Boot Agent PXE-2.0 (build 082 v1.82)
Copyright (C) 2001 NVIDIA Corporation
Copyright (C) 1997-2000 Intel Corporation
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting NVIDIA Boot Agent.

Yukon PXE v1.11 (20031002)
(C)Copyright 2003 Marvell(R). All rights reserved.

Pre-boot eXecution Environment (PXE) v2.1
(C)Copyright 1997-2000 Intel Corporation.

CLIENT MAC ADDR: 00 0E A6 1B 99 ..
GUID: FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF
PXE-E53: No boot filename received

PXE-M0F: Exiting  PXE ROM.
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER
_

```

---

### Post by hansdown on 2009-08-07
> **Cal27 said:**
> Oh, and here's exactly what happens when I try to boot:
```

Verifying DMI Pool Data . . . . . . .
Boot from CD :
Boot from CD :

NVIDIA Boot Agent PXE-2.0 (build 082 v1.82)
Copyright (C) 2001 NVIDIA Corporation
Copyright (C) 1997-2000 Intel Corporation
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting NVIDIA Boot Agent.

Yukon PXE v1.11 (20031002)
(C)Copyright 2003 Marvell(R). All rights reserved.

Pre-boot eXecution Environment (PXE) v2.1
(C)Copyright 1997-2000 Intel Corporation.

CLIENT MAC ADDR: 00 0E A6 1B 99 ..
GUID: FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF
PXE-E53: No boot filename received

PXE-M0F: Exiting  PXE ROM.
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER
_

```

I think it's telling you there is no file system on your hard drive.

It's asking you to put an install disk in the drive.

I'm hoping you planned to install the operating system of your choice.

The one you decided to install may be corrupt.

Can you burn a new one?

Burn it at the slowest speed that you can.

---

### Post by Cal27 on 2009-08-07
> **hansdown said:**
> I think it's telling you there is no file system on your hard drive.

It's asking you to put an install disk in the drive.
Strange, I can access the drive from the LiveCD with absolutely no problems.

---

### Post by Cal27 on 2009-08-07
Could this be a problem with grub?

---

### Post by hansdown on 2009-08-08
It could be grub, or any number of problems.

Did you check the MD5SUM?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

It's easier to burn a new copy.

---

### Post by Cal27 on 2009-08-08
> **hansdown said:**
> It could be grub, or any number of problems.

Did you check the MD5SUM?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

It's easier to burn a new copy.
Sorry, I don't understand. My CD is fine, but my computer is refusing to boot off a hard drive.

---

### Post by hansdown on 2009-08-08
Hold ESC while it boots up.

You should be able to see your grub info.

---

### Post by Cal27 on 2009-08-09
Okay, I've solved the problem. I'm still not quite sure what the problem was, but I think it had to do with grub. I just put a new Ubuntu installation on the disk and I can boot up into both installations fine now. Thanks for all the help handsdown!

---

### Post by hansdown on 2009-08-09
Glad you fixed it Cal27.

---

### Post by j_arquimbau on 2009-08-20
Try this:

Insert a live CD, open a terminal and type:

$ sudo grub

grub> find /media/disk/boot/grub/stage1

grub> root (hdx,y)
where 'x' and 'y' must be replaced by those obtained in the previous stage

grub> setup (hd0)

grub> quit

---

