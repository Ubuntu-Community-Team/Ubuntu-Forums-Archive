---
title: "Removing USB hard drives takes too long"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by tyke on 2007-02-04
HI, I wondered if anyone could shed some light on this problem for me.

When I eject a USB HDD or flash memory stick by right clicking on it's icon, I find that the "removing device" dialog can take an extremely long time to disappear. It seems (although I haven't timed it) to take about the same time as initially copying the files did.

All the time the "removing" dialog is displayed, the activity light on the HDD is flashing, so it's clearly accessing the drive and doing *something*, I just have no idea what. All of the USB HDDs I've tried display this behaviour, but only under Linux. 

I'm using Edgy, if thats at all relevant. I would really appreciate any help anyone can offer. I use USB HDDs a lot, and this is essentially doubling the time it take me to copy files.

Thanks in advance.

---

### Post by mihail on 2007-03-31
I'm having the exactly same problem with Ubuntu Edgy. With Windows XP / anything, removing USB device (memory stick or whatever) takes only couple of seconds. With Ubuntu, it takes as much as I wasted my life to wait while copying the files to the USB device.

Please someone, help us with this one. If this really is the case with Ubuntu / Linux, I'm heading back to Windows!

---

### Post by Arlanthir on 2007-04-01
From what I know, Ubuntu is more worried with your usb lifespan than windows.. Whereas windows writes the file as soon as you copy it to the usb, Ubuntu makes a list of what files you want to copy and only copies them when you unmount the usb.. I think this is the issue.. You may want to ask some more experienced people though..

---

### Post by jjordan on 2007-04-02
What file system are you using on the USB hard drive?  If you are using an NTFS (Windows XP) drive you are likely to experiance some perfomance problems.  Installing ntfs-3g and making sure it is used on removable media may help.  All of my external drives use the EXT3 filesystem and have no problems.  I use a 4GB SD card (formated with fat32) and copy an approx 50MB video news file over to it every morning, "safely remove" works almost instentaneously.  If you must have easy access from XP I would recommend reformating to fat32 which is much better supported under Linux.  There are downsides to fat32, no security, 2GB single file size limit etc.

-j

---

