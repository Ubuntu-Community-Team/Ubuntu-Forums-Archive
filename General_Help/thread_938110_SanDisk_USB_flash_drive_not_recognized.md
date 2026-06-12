---
title: "SanDisk USB flash drive not recognized"
date: 2008-10-04
forum: General Help
---

### Post by rashby3 on 2008-10-04
I have a USB flash drive made by SanDisk that I can use on a Windows XP PC but not on my Ubuntu Linux laptop. On the side of the SanDisk drive it says, "Cruzer mini 128 MB".

When I plug it into a USB port on the Linux laptop, it lights up, indicating it is getting power, but the laptop can't see it. If I try rebooting the laptop with the flash drive plugged in, the boot sits there suspended until I pull the flash drive out, then the boot finishes.

On the other hand, I have a slightly older 128 MB flash drive made by a different manufacturer that I can use in either my Windows PC or my Linux laptop. The writing on the side of this one is faded, so I can't tell what company made it.

I was thinking of going out and buying a much bigger USB flash drive but--given my problem with the SanDisk drive--I am worried that it might not work on my Linux laptop.

Is there information available somewhere on which USB flash drives do and do not work on Linux?

Alternatively, is there anything I can do with my Linux system to help it "see" the SanDisk drive? (Or some other USB drive I might buy?)

Thanks very much.

---

### Post by silkstone on 2008-10-04
Does the SanDisk drive have any security software on it? Sometimes you have to disable this in Windows first, before Ubuntu will read it.

Have you tried looking at the drive with Gparted? That should tell you if the drive is recognised, even if it can't be read.

Currently I'm using a SanDisk Cruzer Micro 4GB and a Patriot Xporter 8GB, both of which work fine with Ubuntu - although I did first remove the U3 software from the SanDisk drive on XP.

---

### Post by ajgreeny on 2008-10-04
Have you always removed the drive properly in windows, ie clicking on the little icon the system tray and choosing "Remove safely"?  If you don't do it that way the ntfs file system puts a lock on the drive which means it can not be mounted and read by Ubuntu, or other linux distros.

---

### Post by rashby3 on 2008-10-05
To those who offered suggestions: thanks for the help .

There was no security software on my USB drive.

I also made sure I removed the drive from my XP machine using the "Safely Remove Hardware" icon in the system tray, but it had no effect on my problem.

What finally worked for me is the following:

I attached the drive to a Windows Vista machine and then removed it using that machine's "Safely Remove Hardware" icon. When I then tried it in my Ubuntu laptop, it was recognized.

Not sure what is going on here, but XP and Vista apparently work differently when "safely" removing hardware.

---

