---
title: "Automount NTFS"
date: 2011-03-08
forum: Hardware
---

### Post by Red Dog 99 on 2011-03-08
I've read over all the stuff I can find on this subject, but none seam to have the exact answer. 
THE Problem: Mount a NTFS HDD on a computer with a hot swap tray.
                     UBUNTU 10.10 Maverick Server (CLI only)
                     The physical HDD could be one of twenty SATA drives.
                     The drives could be different capacities, but always NTFS
                     Mounting to the same mount point ok
                     NO reboot to mount or unmount drive

Yes the hardware supports ACHI and it does work. Working with the FSTAB doesn't work because I don't know what drive it is. I can do this process manually.
```
mount /dev/sda3 /mnt/sd1 
```
NTFS-CONFIG appears to work only with GUI (not available)
AUTOFS works with know local or remote dive, This is neither.
UDEV appears to be not available in Maverick
FUSE might work
and is NTFS-3G required ?
Their is no network involved with this process.
Their is no Windows operating system on this computer.
:popcorn:

---

### Post by Red Dog 99 on 2011-03-08
Sorry I left out another point NO RAID is involved with any drive.
NO backup drive or scripts, and no other operating systems. 
These swappable disk only contain data.

---

### Post by Red Dog 99 on 2011-03-11
I getting a little depressed with this problem. I tried working with the USB memory sticks as a simpler step to see whats going on.  The reason I switched to UBUNTU server was to mange a large collection of media and data. This information is spread over numerious HDD drives, CD/DVD and USB memory sticks. If I can't swap them around as need then whats the point of a server???
OK, enough rant! 
For the USB problem I tried Autofs. The auto.master contains:
    "/mnt/usb   /etc/auto.usb --t 5"
The auto.usb file contains:
   "*      -fstype=vfat, rw    :/dev/sd&"
Guess what it doesn't work. I need the wild card because of the selection available, twelve USB port and twenty son USB memory stick plus other devices.
If I use:
    "USB1   -fstype=vfat, rw    :/dev/sdd1"
in the auto.usb file it works.
Part of what is so frustrating is that all this is seamless in the desktop version.

---

