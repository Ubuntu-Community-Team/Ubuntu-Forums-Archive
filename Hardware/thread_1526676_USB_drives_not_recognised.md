---
title: "USB drives not recognised"
date: 2010-07-08
forum: Hardware
---

### Post by subi211 on 2010-07-08
Yesterday I finally gave up with KDE and moved from Kubuntu 10.04 to Ubuntu 10.04.  Everything was going fine until I tried plugging in a USB pen drive.  Ubuntu did not recognise it, nor the other four drives of varying sizes and filesystems that I subsequently tried.  Kubuntu could recognise and mount them all, and still can (I kept the HD I had Kubuntu on so I swapped it back into the machine to check).

So what's KDE doing that Gnome can't?  I've tried usb-storage in /etc/modules.  I've tried modprobe usb-storage.  I've tried update-usbids.  lsusb doesn't see the drives in Ubuntu but does in Kubuntu.

It can see the USB keyboard and mouse, but I can't copy files to those.  Does anyone have a solution?

---

### Post by dabl on 2010-07-08
Are you running Ubuntu in a Live CD mode, or installed on a hard drive?  If it is installed, try booting the Live CD, and see if USB devices are recognized when you plug one in.

KDE uses "device-notifier" and it has some different settings.  I'm not sure what Gnome uses.

---

### Post by subi211 on 2010-07-08
I'm running installed.  I just tried booting from the Live CD and that wouldn't recognise any drives either.

---

### Post by dabl on 2010-07-08
What are these "various filesystems"?  I'm not sure Ubuntu will automatically mount NTFS (not sure Kubuntu will either, but it might).  But one would still expect to see it on the lsusb list.

With one of the problematical USB drives connected, try in a terminal ```
sudo fdisk -lu
```

If it shows the drive on the list, then the issue is only the mounting.  If it is not FAT32 or ext3/4 format, then you might be stuck mounting it manually.

---

### Post by subi211 on 2010-07-08
I've got some FAT32, some FAT, one NTFS.  No joy with fdisk -lu.

All the stick do display one similar symptom:  The lights on them flicker for a moment, then go out.  On Kubuntu, Windows and Gentoo (which is the target for the files I'm trying to copy on to the stick) the lights flicker, then stay on.

I've got no problem with mounting them manually (I have to do that in Gentoo anyway), but I'm not even seeing any devices to mount.

---

### Post by dabl on 2010-07-08
> **subi211 said:**
> 

  No joy with fdisk -lu.



That's a bad thing.  Sounds like a kernel module is missing, but I don't know which to suggest looking for.  

So the Kubuntu, Windows, and Gentoo systems are installed on that same computer?  If so, then that proves there's nothing wrong with the hardware.

Do you have any other Ubuntu kernel versions available to boot?

---

### Post by subi211 on 2010-07-09
Well, the Gentoo install is on another board in an arcade cab in my sitting room (minimal install because it's only got 1GB available to it, too small for Ubuntu ;) ), and I was using yet another PC to check with Windows.  But I checked with Windows, Ubuntu and Kubuntu on the offending PC.

This is where it gets weird:  This morning I booted the offending machine into Windows and checked the sticks there.  They read fine.  Then I went back into Ubuntu and they didn't read at all.  To make absolutely sure I unplugged the USB mouse and put a stick in the slot it was in.  It worked!  Then I tried it in the other slot which had had the mouse plugged into it.  That then worked too!

So the solution I seem to have come up with is to plug a USB mouse into a socket I want to get a stick to read from.  I'm puzzled, the mouse must tickle something extra that the sticks don't, but at least they work now!

---

