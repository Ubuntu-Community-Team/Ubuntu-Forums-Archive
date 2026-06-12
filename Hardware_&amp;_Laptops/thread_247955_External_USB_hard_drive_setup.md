---
title: "External USB hard drive setup"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by maurizio on 2006-08-31
Hi,

I am new to Ubuntu and would be very grateful if you would help me setup properly an external USB hard drive (40 Gb SmartDisk Firelite).
I want to use it as a backup unit, onto which files would be updated using rsync. There are many things I do not understand.

Initially, I formatted it using fdisk and mkfs (with the ext3 file system) and everything seemed to be fine.
I also browsed the web for how to name it persistently using udev rules and the etc/fstab settings, which worked perfectly.

But then, for some reason, I decided to take a look at it using gparted.
That application revealed that something was not formatted correctly (an exclamation point appeard in the description of the partition, with some warning message).  So I decided to re-format it completely using gparted.

After rebooting, now when I go to "Places -> Computer", I see TWO USB Hard Drives named "USB Storage 37 Gb" and "USB Storage 37 Gb (2)".
If I run the command "sudo mount /dev/Firelite /media/Firelite", on the desktop the icon appears correctly with just one device, named Firelite (the name I gave to the unit).

My question is: can I trust this to be a stable backup system?
Did I do things correctly? So, why there appear to be two usb disks?
Also, why fdisk seemed to have missed something in the formatting process?
Would you recommend ext3 or another file system (xfs)?

Last question: when I close the lid of my laptop, I would like the USB drive to stop, but this does not seem to happen.

Thank you SO much in advance for your help!

---

### Post by toasterofirony on 2006-09-01
I'm a little confused as why you have done so much work to get this to work. I've just done something similar, in that I have bought an external enclosure  (USB 2.0 connection to my Linux box) for a spare internal 3.5" HDD I had lying about(formatted in NTFS, no less :P) and for me it was a simple case of plugging everything in and turning it on. I've done the same thing with my Pa's external USB HDD (a proper job, not a put-together one like mine).

Why were you fiddling with fstab? You can just right-click and rename, surely? And why are you manually mounting it? If it's USB, it should be just a case of plug and play.

Sorry I can't answer your questions directly, but perhaps these things are worth thinking about?

---

### Post by maurizio on 2006-09-01
Thank you for your reply!

The reason for all this work is that, initially, I just plugged it in and it seemed to work (formatted FAT32) ... until I tried to backup my entire home directory in linux (around 4 gB).  The disk started behaving in a very weird way: in the middle of the backup, I would lose access to the disk.
Then I realized that FAT32 does not support owners and permissions.

So I decided to format it ext3 using fdisk, which worked.
Yesterday, though, I wanted to make sure everything was ok and used gparted to take a look at this hard drive and it gives me a warning:

"Warning! Unable to read the content of this filesystem! Because of this some operations may be unavailable. Did you install the correct plugin for this filesystem?"

This is strange, as the hard drive works perfectly and I can backup any time I want using my rsync scripts.

Do you think I can trust fdisk to have done a good job?

Thank you SO much once again for your help!

---

### Post by toasterofirony on 2006-09-01
No problem. I would suggest (if you have access to such a device) try formatting it on an XP box under NTFS and see where that gets you.

I don't know if this is the best way to do it, but it works for me :)

---

### Post by maurizio on 2006-09-01
Yes, I had also read somewhere that people format their external hard drive in Windows first, and then they make a Linux file system on them.
Perhaps it's because Linux doesn't have a good partition software??
I don't really know.

Thank you so much for your help!:p

---

### Post by toasterofirony on 2006-09-03
Honestly, I couldn't say for sure, but mine works fine. I'm not sure you have to worry about making it ext3 at any point and if it works with a minimum of fiddling, so much the better, y'know? I hope you figure out a cure for your problem :)

---

