---
title: "Help adding an external usb hard disk"
date: 2006-01-24
forum: Hardware &amp; Laptops
---

### Post by david_finlayson on 2006-01-24
Wow! this is turning out to be harder than I imagined. I purchased an external enclosure for a 200G IDE hard drive. The idea is to use the USB2 cables to plug it in and transfer data between my various computers (both windows and Linux).

I started with a single FAT32 partition for the entire 200G. Seemed to work fine in Ubuntu on two different computers. But when I plugged it into an XP box, XP wouldn't mount the disk. It showed that there was a new USB2 device, and the disk manager thing (can't remember what it is called) showed the entire 200G drive, but it called it unknown or unrecoginized.

I got frustrated and said screw that, I don't need windows compatibility that bad. So, back in Ubuntu, I reformated the disk as a single ext3 partition. Linux saw the disk, but only root had permision to write to the disk. I looked on Google for hours for a solution to this. It's probably is possible by adding lines to fstab, or maybe lines to one of the UDEV configurations, but man this is complicated.

I said, screw THAT (again!) and decided to go back to FAT32. At least I don't have permision problems. Now, Ubuntu can see it just fine, but now it mounts the disk twice!!?? I've got two icons for the volume. usbdisk and usbdisk-1. I've rebooted, I've pulled the cables out. I am at my wits end.

Is there a step-by-step guide to getting an external hard disk (1) properly formated and (2) properly configured to work with Ubuntu (and hopefully Windows XP too)?

I'd greatly appreciate a stupid-simple intro to this stuff. 

Thanks

---

### Post by lisje on 2006-01-25
I also got an 200GB external hard drive, also on USB and I formatted is so that it has a small 20GB partition for files to be exchanged between linux and windows.
The other 180GB is an xfs partion (it used to be an ext3 partition) which only linux can read (because I spend most of my time in linux.

When I plug the drive into my system it gets mounted allright.
(could it be that windows couldn't read your fat partition because it was too big??? windows only allows it to be smaller then 35GB, I think)

here's the relevant piece of my fstab:
```
/dev/sdb1       /media/files     vfat    noauto,iocharset=utf8,umask=000,defaults,noatime,user        0       0
/dev/sdb2       /media/mfti     xfs     noauto,defaults,noatime,user        0       2
```

hope it helps a bit.
Greets,
Lisje

---

### Post by david_finlayson on 2006-01-26
I got it working (mostly, see below) by using Gparted to create a single 200GB (186Gib) primary partition in ext3 format. (I also formatted the partition using the Disk Manager tool but I don't know if this was necessary).

Then, unmount the drive using pumount /dev/sd1
unplug the USB, reboot (for good measure) and reconnect the USB.

Now, it mounts automatically (using pmount?) and places a directory in /media/usbdisk-1.

I don't think there is any need for an fstab line in this situation (although it might be useful for customizing the mount)

However, when I right-click the icon to unmount the drive I get an error:

Unable to eject media
eject: unable to eject, last error: Invalid argument

It seems to unmount though as requested after clearing the error box.

If instead I use pumount /media/usbdisk-1 I do not get an error. What is happening here?

I have given up on windows compatibility for this drive for the moment.

---

