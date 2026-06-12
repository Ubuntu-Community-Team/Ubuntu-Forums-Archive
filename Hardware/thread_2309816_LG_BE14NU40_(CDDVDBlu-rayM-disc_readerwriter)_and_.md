---
title: "LG BE14NU40 (CD/DVD/Blu-ray/M-disc reader/writer) and Oryx Pro power problem"
date: 2016-01-13
forum: Hardware
---

### Post by Savak on 2016-01-13
I've been having a problem with an LG BE14NU40 CD/DVD/Blu-ray/M-disc reader/writer and a new Oryx Pro from System76 (aka a Clevo..I think P650SE / Sager NP8651 according to [this]("http://ubuntuforums.org/showthread.php?t=2305511") thread), running Ubuntu 15.10. I've passed it by System76 support but thus far they have no such drive to test with and suggested I try the hive mind over here; I only know "their" test drive has been working fine, but I don't know what is being used to test. 

The particular drive at issue is an external drive with its own power supply, connected to the laptop by a USB cable. The drive powers on fine, and works as expected on a Dell Latitude E6530 work laptop running Windows 7 Enterprise as well as an older Samsung laptop (apologies --  I think it's a Q320? but I don't have it as I write this) running Ubuntu 15.10, for as much as I've tested with those systems (connects, reads a CD, will spin down, then spin back up when the disk is accessed -- no unexpected unmounting or power down). Both of those "other" laptops also have an internal CD/DVD drive, while the Oryx Pro does not. When the LG drive is connected to the Oryx Pro it can be turned on normally, eject button works, and it will sit there for hours with the eject button functional IF there is no disk in the drive. Once a disk is put in, the laptop will automatically mount the disk and I can access and use it as normal UNTIL it spins down for the first time. As soon as the drive spins down the disk, it immediately is unmounted and almost always is somehow soft powered off -- the eject button ceases to work and I have to power cycle it with the switch or power cord. Rarely instead of fully powering off it will still unmount the drive, but then irregularly spin back up and sometimes reconnect, but still eventually spins down and also powers off. 

During initial testing I thought the power supply was the problem, as it appeared to connect then disconnect and power off very quickly, until I realized the link to what appears to be an otherwise normally timed first spin-down (i.e., it has not shut down while in the middle of actually doing something, whether that's ripping a video or burning a disk, but immediately did so as soon as those tasks completed and it went to its first spin-down), and was able to see that while the drive is being accessed (for reading or writing) it will remain connected, powered, and doing its job. And, of course, that no problem has been noted while testing with either of the other 2 aforementioned laptops, nor that the drive has ever soft powered off by itself when simply turned on and a disk inserted when the USB cable is not connected to anything (it still spins down, but the eject button continues to be powered and work). 

Testing the Oryx Pro with a Rosewill ROD-EX002 external drive powered only by USB yields expected results; disk mounts, spins down at a reasonable time, does not disconnect or power down, and will spin back up again upon trying to access it. 

I've made some attempts at changing 'autosuspend' settings globally, to no effect (and the settings for that, as well as 'autosuspend_delay_ms', and really everything I have been able to identify so far, are identical to those on the older working Ubuntu 15.10 laptop). I have also been unable to identify anything in the BIOS settings which have anything to do with drive power. But I'm at a loss as to why the externally powered LG drive is both disconnecting and powering down at the time of an expected normal spin-down, except that it appears to be doing so at only the behest of the Oryx Pro. 

Any ideas, or similar issues, out there? Or anyone with the same laptop hardware successfully using any externally powered optical drive? 

(On a tangential note, I'm actually quite fond of the Oryx Pro; I know there are not many reviews out there for it yet, but in about a month of ownership and pretty much daily use this is the only unresolved issue I've had.)

---

### Post by Savak on 2016-01-20
In the absence of any better ideas, I've given up on the LG BE14NU40. I suspect it is an oddity with my particular hardware/firmware/BIOS configuration communicating with that of the drive, as the drive otherwise seems to work, including on a different Ubuntu system. I have since obtained a Samsung SE-506CB, powered over USB rather than an external power supply like the LG. Under limited testing it has worked as expected -- at the least, no disconnection/power-down upon spin-down, and it has read at least one blu-ray disk, though I have not attempted any burns. But if I run into a problem at least it's not the same problem I was having with the LG.

---

