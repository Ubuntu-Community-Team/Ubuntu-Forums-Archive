---
title: "Ubuntu 8.10 System Hosed Kernel panic on 2.6.27-7 Kernel"
date: 2008-11-25
forum: General Help
---

### Post by grunge09 on 2008-11-25
I have a problem.  System was updated like 2 weeks ago via update manager to 8.10 and all was hunky dory until today.  In fact everything has been running fine since I installed Ubuntu 6.06 LTS almost a year ago.  Been updating ever since.  

I did a shut down, and went out for the day.  Came home and powered up the system and I get the folloring errors:

0.115331 ACPI: Aborted because junk in compressed file
1.041438 Invalid compressesd format (err-2)
1.060063 Kernel Panic - not synching VFS: Unable to mount root fs on unknown-block (0,0).  


Rig is:

Amd 3200+ CPU
AGP Geforce Fx 5200 Video Card
512 MB RAM
120 MB SATA Hard Drive
DVD Rom Drive
DVD / RW Drive.  

I found that If I choose an older kernel the system will boot, but complain that can't load NVIDIA stuff.  I can run the system with the older kernel in reduced graphics mode.  

I booted into an older kernels recovery mode and ran Fsck.  Rebooted and that did not fix the problem.  

I have been running Ubuntu now for about a year and this is the 1st time I have run into this problem.  

Can anyone help???

The FIX for me at least after some searching, I found the initramfs was hosed.  

so I opened a terminal and ran...

sudo update-initramfs -c -k 2.6.27-7-generic

Exited and rebooted and the system boots fine now in the newest kernel.  Hope this helps folks out.

---

### Post by grunge09 on 2008-11-27
Anyone have an answer?

---

### Post by AntonioAzevedo on 2009-03-05
Same here on kernel 2.6.27-11, updated and can't boot anymore.

This is exactly what I get:

[ 0.043899] ACPI: Aborted because junk in compressed archive.
[ 0.586706] i8042.c: No controller found.
[ 0.652181] invalid compressed format (err=2)
[ 0.659561] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

Can't boot with 2.6.27-7 Kernel either....

Running on a Macbook Pro5,1

---

### Post by opensourcederry on 2009-03-06
Same here as well.

Fresh installed 8.10, let it do it's updates and got the kernel panic VFS etc message.

The updates seem to install a new kernel but I can boot ok using the previous kernal via grub.

osd.

---

### Post by jimbean on 2009-03-06
i am no linux guru but i would try to disable the advanced power management
in the bios {acpi} and see if that helps i had trouble with it myself

if that does anything to help i would try to search the ubuntu forums to fix the acpi issue i found something about a month ago that fixed my system
but i had to search and search and search and i dont know where but i found a fix

---

### Post by onesojourner on 2009-04-30
I am having this issue  too.

---

### Post by cazacugmihai on 2009-05-22
Same here on kernel 2.6.28-12.

This is exactly what I get:

[ 0.021330] ACPI: Aborted because invalid comressed format (err=2).
[ 1.718233] invalid compressed format (err=2)
[ 1.721449] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

But it works if I boot with 2.6.28-11.
Is there a solution for this problem?

Thanks.

---

### Post by codywohlers on 2009-06-30
I had the same problem on a 9.04 64-bit server after an upgrade from 2.6.28-11 to 2.6.28-13.  Well actually my second line was "crc error" instead of "invalid compression format" but I got the error even when I tried to boot into the previous kernel.  

Using the command line in grub I edited the new kernel boot option to boot from /dev/sdxy instead of a uuid.  It worked.  After that first successful boot I can now boot with the uuid again.  Strange...

---

### Post by rogercruse on 2009-07-02
Just run Update Manager to patch my 9.04 version running from a USB and got the same messages when I rebooted.

---

