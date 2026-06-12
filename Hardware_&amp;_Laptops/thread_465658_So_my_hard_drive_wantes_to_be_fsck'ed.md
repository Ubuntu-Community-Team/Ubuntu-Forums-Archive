---
title: "So my hard drive wantes to be fsck'ed"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by Slace on 2007-06-05
Every time I boot my laptop running Kubuntu 7.04 (Feisty) I get to the "Checking root file system" stage and then am told the following: 
fsck 1.40-WIP (14-Nov-2006) 
/dev/hda1: Superblock last write time is in the future. FIXED 
/dev/hda1 contains a file system with errors, check forced. 


Then it does the check, ticks along to about 90% or so and then says that it found errors and will now reboot. 

So it reboots and the process happens all over again . 
Now, this is rather frustrating as I now can't use my laptop! 

I've tried booting a Knoppix disk I have and doing a fsck on the drive partiton (I have 2 ext3 partitions on this drive, hda1 is just the root partition). 
The fsck ran fine, did all it needed to do, I rebooted and still no love. 

I'm not very knowledgable regarding this side of linux, so I've tried the two things I know (knoppix and yelling at it). 
Does anyone know what I can do to fix it, I really don't want to have to re-install :(

---

### Post by yabbadabbadont on 2007-06-05
The filesystem write time in the future error is probably because you have your bios clock and ubuntu configured to local time.  Which is what you are supposed to do if you dual-boot with windows.  The error is because the root filesystem is checked before the system clock is configured, which is when your timezone is taken into consideration.  If you aren't dual-booting with windows, then make sure that you have your bios and system clocks configured for UTC.

---

### Post by Slace on 2007-06-05
How do I check/ change my ubuntu time to UTC?

---

### Post by yabbadabbadont on 2007-06-05
I'm not positive that there isn't something else wrong with your filesystem too, but it shouldn't hurt anything to switch your clock to UTC (other than Windows will show the wrong time).

```
/home/daffy $ cat /etc/default/rcS 
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no

```
Edit that file and change the UTC value to "yes" like I have it, then reboot.  You will need to use either sudo or gksudo to start your editor or you won't be able to save your changes.

---

### Post by Slace on 2007-06-05
well since I have to do it via Knoppix (as I can't book Kunbutu at the moment) I just had to mount the drive.

But when mounting it told me there were file system errors and to run e2fsck, which I'm now running.

I'm not 100% sure if my bios supports UTC time either, but I'll check on reboot

*Edit:

After the reboot I missed getting into my bios and Kubuntu started to boot. This time I got a different issue (to do with one of my hard drives missing, when its not really missing, it just went from hda2 to sda2 and now its back to hda2!).
I'll edit my /etc/fstab and reboot, but hopefully its all fixed :)

*Edit 2:
Well its all working  again. But for some reason my sound is not working, but that's a problem for another thread...

---

