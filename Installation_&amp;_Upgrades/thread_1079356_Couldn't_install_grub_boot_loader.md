---
title: "Couldn't install grub boot loader"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by fibyr on 2009-02-24
Hi,

I'm new to ubuntu but I really like it, I installed it on my desktop and an older laptop for my son no problem, but I'm having trouble installing it on my laptop (AMD64 x2, vista-yuck)](*,) i've tried the cd and Wubi - then last night I downloaded the alternate cd that was going fine but it wouldn't install the grub boot loader it said:-

boot manually with the /vmlinuz kernel on partition /dev/sda9 and root=/dev/sda9 passed as a kernel argument :confused:

can anyone explain to me exactly how I do that please, :redface:

Fiona

---

### Post by Therion on 2009-02-24
Well the alternate CD is fine but maybe we don't need to go there just yet.  When you try to install from the standard LiveCD, what prevents you?  Do you get an error message, a system lock-up or what?  

Also, do you know, or can you get, some of the basic specs of the PC you're trying to install on?  How much RAM it has what graphics chipset or video card it's running could prove very helpful.  Anything else you could get would icing.

Sometimes getting a LiveCD to boot is just a matter of a tweak on the GRUB line or something simple like that.  And installing from the LiveCD really is my preferred method.

---

### Post by fibyr on 2009-02-24
When I try the live cd it stops before it gets to ubuntu install screen does nothing - it says something like, aperture beyond 4GB ignoring then stops

It's an iQon laptop
Processor AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53, 1700 Mhz, 2 Core(s), 2 Logical Processor(s)
Graphics NVIDIA GeForce Go 6100?
Total Physical Memory	1,982.06 MB
Hitachi HTS541612J9S SCSI Disk Device 111.79 GB

thanks

---

### Post by Therion on 2009-02-24
First thing to look at is your install media; this is probably the single biggest source of problems like this one.  

Try re-burning the CD at a slow speed (like 8x or 16) and retry installing.

---

### Post by fibyr on 2009-02-26
i turned off bios legacy support and it works now

---

