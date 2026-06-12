---
title: "How do I get a USB drive to automatically reconnect on boot?"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by Hercules on 2006-11-27
I am running Xubuntu 6.06.1 and would appreciate some advice on getting an external USB hard-drive (formatted in FAT32) to reconnect automatically when the computer boots.

The problem is slighlty strange... When I boot the computer I can see the device as a link on the desktop, but when I try to navigate through the file system (via "/mnt/usb" using Thunar) to access files on the hard-drive, I cannot see any files listed.

However, if I then use the link on the desktop and double-click on it to open the device, and then go back through the file structure (i.e. via "/mnt/usb") to access files, I can then see and open them... It's almost as if I need to "wake up" the drive before I can access it!

I suspect the problem is related to my fstab line?

This is what I have:
/dev/sda1 /mnt/usb vfat auto,users,fmask=0111,dmask=000 0 0

I'm a Linux newbie and have got a bit confused about all the settings in the fstab entry. In particular the "options" part seems particularly confusing, and I've read lots of conflicting information on various forums!

For now, I'm not too worried about security. I'd like to get it running first before then learning about the details of Linux security, and applying tighter controls as necessary.

Any help appreciated!

---

