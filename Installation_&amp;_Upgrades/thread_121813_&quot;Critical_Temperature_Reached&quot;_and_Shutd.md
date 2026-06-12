---
title: "&quot;Critical Temperature Reached&quot; and Shutdown During Install With Low Temperature"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by GeekStarPilot on 2006-01-26
Hello learned forum members.

I am trying to install Ubuntu 5.10 on a newly formatted PC.

Preliminary setup worked OK but after reboot to start second stage of install the PC always shuts down after reporting a "Critical Temerature Reached" message.

The reported temerature was 42 deg C first time and 34 deg C seond time before I gave up and headed to the forum.

These temeperatures are correct (i.e. the match the temperature reported by the BIOS sensor screens) but they are significantly below the maximum for shutdown (55 deg C).

I have checked all CPU fans and made sure that there was no build up of dust on heatsinks.  Everything is OK.

It appears that there is some sort of bug because Ubuntu should not be shutting down the the PC at such relatively low temeratures.

The system details are:

SuperMicro P6DLS MoBo
Dual PII 300 CPUs
All Adaptec SCSI HDD and CD drives
1 x 9.2 GB HDD
1 x 4.0 GB HDD
1 x DVD-ROM drive
1 x CD-RW drive
1 x 3.5in FDD drive
512kB RAM
Creative AWE64 Gold Sound Card
IEEE 1394 PCI Card
nVidia TNT2 Ultra AGP Video Card

Finally some additional information.  I have successfully installed Windows 2000 Server and a few other types of Linux on this machine in the past without any unnecessary temperature shutdown problems.

I would appreciate any suggestions from the group on how to get around this problem.

Thanks in advance to all who reply.

Regards,
Steve

---

### Post by adwait on 2006-01-26
Those temperatures are really low :p Ambient summer time temperatures sometimes reach those values around here!

Anyway, coming to the point......wierd! Try turning off the temperature protection in the BIOS setup temporarily.

---

### Post by Howcomes on 2006-01-26
yea 42 isnt too bad, it isnt until 60-70+ you sould be worrying, change the temperature shutdown/warning settings in your BIOS

I'm going to assume you know how to get into your bios....

---

### Post by megamania on 2006-01-26
[QUOTE=GeekStarPilot]It appears that there is some sort of bug because Ubuntu should not be shutting down the the PC at such relatively low temeratures.
...
Finally some additional information.  I have successfully installed Windows 2000 Server and a few other types of Linux on this machine in the past without any unnecessary temperature shutdown problems.
[/QUOTE]

I don't think this has anything to do with ubuntu or any other os, nor with the fan (because the temperature is low!).

The "critical temperature" is usually handled directly by the BIOS, and the shutdown is forced by the BIOS taking over. If you don't find a solution, you may want to try resetting it by backing up your bios settings and removing the power cord and the battery for a few minutes.

You are supposed to know what you're doing though!  ;-)

---

### Post by MJN on 2006-01-26
It doesn't sound like a BIOS issue to me, particularly given the repeatability of the problem.
 
I'd be more inclined to suspect a dodgy ACPI implementation but how to fix that mid-install I don't know (someone else can jump in here).
 
Once up-and-running, I would've suggested adding **acpi=off** to the kernel line in /boot/grub/menu.lst.
 
Perhaps in this mid-install state you could boot from a LiveCD and edit the config file (and reinstalling it with grub-install)?
 
Of course, this is not the ultimate solution as you'd likely want acpi to be functioning properly, however it may at least distinguish between this being a hardware or software issue.
 
Mathew
 
P.S. A web search revealed that removing the 'thermal' module from** /etc/default/acpid/** might do the trick.

---

### Post by megamania on 2006-01-26
[QUOTE=MJN]It doesn't sound like a BIOS issue to me, particularly given the repeatability of the problem.
 
I'd be more inclined to suspect a dodgy ACPI implementation but how to fix that mid-install I don't know (someone else can jump in here).[/QUOTE]

hmmm. so now I'm tempted to delete my previous post.  :-(

---

### Post by MJN on 2006-01-26
Ahh, but I could be wrong and you might just save his PC from catching fire... ;)

---

### Post by GeekStarPilot on 2006-01-28
Here is an update.

It appears that the implementation of ACPI in my (older) motherboard is probably not fully compliant and therfore confuses the ACPI drivers in Ubuntu.

I turned off ACPI and turned on APM in the BIOS, reformatted the drives and installed using the "pci=noacpi" flag during the Ubuntu installation.

Everything went very well.

The boot log shows a failure of ACPI but there appears to be no impact on the operation.  I understand that can make some modification to how the PC boots to eliminate the ACPI failure messages.

I understand that I don't have all of the power management stuff but this is just a play linux box so it doesn't really matter.

Thanks to all who replied to my post.

Regards,
Steve

---

