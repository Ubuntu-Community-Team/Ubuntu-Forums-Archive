---
title: "Grub Error 21. Machine won't boot."
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by ETW Grumpy on 2009-07-15
I tried to install Ubuntu 8.10 in a dual boot with Win XP on a Dell Dimension 2.4 GHz desktop. It froze during the install, so I rebooted it and started getting Grub error 21. Now it won't boot at all. Did I just make a 9 lb doorstop out of this thing?

---

### Post by Vakman on 2009-07-15
There is always a fix. All right, so we will need some more information shorty. GRUB Error 21 means that GRUB can't find the disk to boot from. A really easy fix for you is to go to [http://www.supergrubdisk.org](http://www.supergrubdisk.org) and download it. It will usually fix your problem automatically. You just have to boot from the CD. There are also instructions on the website. That would be your easiest choice. 
Or 
Boot from your Ubuntu LiveCD.
Then, open up a terminal and type ```
sudo fdisk -l
``` fdisk -l and find your Linux boot partition from the list like it might be sda1 or something, where ever you installed it.
Then enter ```
grub-install /dev/sda
```
Post back. Still easiest solution is SuperGRUBdisk. It does things automatically and I am not completely confident in the way I just told you but it will likely work.
Post back and tell us how either one goes :)

---

### Post by ETW Grumpy on 2009-07-15
I will try that and post back. Thanks.

---

### Post by ETW Grumpy on 2009-07-15
Downloaded and burned Grub Superdisk. Tried it in both CD drives. Still get this:

Phoenix ROM BIOS PlusVersion 1.10 A05
Copyright 1985-1988 Phoenix Technologies Ltd.
Copyright 1990-2003 Dell Computer Corporation
All Rights Reserved

Dell System Dimension 2400 Series
BIOS Version A05
[www.dell.com](www.dell.com)

Diskette drive 0 seek failure
GRUB Loading stage 1.5.

GRUB loading, please wait
Error 21

I've also tried booting with the Ubuntu CD in, same results.

---

### Post by merlinus on 2009-07-15
Boot from the live cd, open a terminal and post results of

```
sudo fdisk -l
```

Another thing you miught do is to mount your ubuntu partition using nautilus, and post results of:

```
cat /boot/grub/menu.lst
```

---

### Post by ETW Grumpy on 2009-07-15
> I've also tried booting with the Ubuntu CD in, same results.

I can't get anything to boot or run.

---

### Post by ETW Grumpy on 2009-07-15
Anyone else have an idea?

---

### Post by merlinus on 2009-07-15
Press F12 at startup to select booting from cd.

---

### Post by ETW Grumpy on 2009-07-15
Tried that, doesn't work. If I reset my CMOS, will it do away with GRUB?

---

### Post by merlinus on 2009-07-15
Look in your bios (cmos settings) to ensure that the cd drive is set to boot before your hdd.

Other than that, if you cannot boot from a cd, then how can you install any operating system or run any live cd?

BTW, did you do a checksum on the ubuntu .iso, and burn at no more than 4x?

---

### Post by ETW Grumpy on 2009-07-15
The CD drive was working fine before the Ubuntu install messed up. I installed Ubuntu from a CD that I got from Ubuntu. The CD drive is set in BIOS to boot first.

---

### Post by merlinus on 2009-07-15
It seems highly unlikely that software broke your cd drive.  It may be that the disk was defective, and has created problems with the drive.  Dirt?  Scratches?

Also, you might check that the cables, etc. on the drive have not become loose.

---

### Post by shicy on 2009-07-17
insert LiveCD and boot,then open Terminal and type this (line by line)

sudo grub
find /boot/grub/stage1

(hd0,0) [B]<--- THIS IS RESULT!!!! (something like that)

[/B]then type this:

root (hd0,0)
setup (hd0)
quit


GOOD LUCK!

---

### Post by presence1960 on 2009-07-17
> **ETW Grumpy said:**
> Anyone else have an idea?
By the message you receive you have 2 problems. The first is probably unrelated to your not being able to boot. Your diskette seek failure means your floppy is no good or you have a floppy set to run in BIOS but don't actually have a floppy drive. By GRUB coming up that means one of two things: either your boot order is not correct or you have a problem with your optical drives. I would try booting from another bootable CD/DVD such as a windows disk. See if that boots. If not there is a problem with your optical drives. Check the settings in BIOS to make sure they are indeed set to boot first. Check your connections to the optical drives and the mobo and your connections to optical drives and power supply..

---

### Post by presence1960 on 2009-07-17
> **shicy said:**
> insert LiveCD and boot,then open Terminal and type this (line by line)

sudo grub
find /boot/grub/stage1

(hd0,0) [B]<--- THIS IS RESULT!!!! (something like that)

[/B]then type this:

root (hd0,0)
setup (hd0)
quit


GOOD LUCK!
I think you need to reread this thread from the beginning. If you do you will see that your post was utterly useless.

---

### Post by shicy on 2009-07-17
sorry, i thought that it could help
sorry

---

### Post by presence1960 on 2009-07-17
> **shicy said:**
> sorry, i thought that it could help
sorry
the OP said he can't boot from either optical drive, so how is he going to boot the live CD?

---

### Post by shicy on 2009-07-18
now i see that i made mistake...sorry folks ;)

---

### Post by ShadeS_07 on 2009-07-18
Probably a defective HDD (where the GRUB loader resides)... Try this, turn off and unplug PC's power... open SU's case, unplug the HDD's power cable, boot the PC... you might get an Error 5... turn PC off, replug HDD's power cord and boot back... Just give it a try.. I used to have that problem, and that pretty much solves it... Perhaps, a lil work-around? :popcorn:

---

### Post by ETW Grumpy on 2009-07-24
presence1960, I think this may be the problem because I tried to boot the Windows CD and it wouldn't work. My CD is set to boot first in BIOS, could I have screwed up a setting somewhere else that would make it not work? 

ShadeS_07, I'll try this and see what happens. 

If I pull the HDD and get an external HDD enclosure, would I be able to access the HDD with my laptop, bypassing the whole boot issue?

---

