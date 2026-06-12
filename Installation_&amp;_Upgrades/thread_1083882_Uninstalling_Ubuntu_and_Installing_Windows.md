---
title: "Uninstalling Ubuntu and Installing Windows"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by jey_xoxo on 2009-03-01
If this isn't the right place to post this sorry, I'm new.

We just got a new Dell Mini Laptop running Ubuntu. We are trying to install Windows XP, but it doesn't want to load. I've tried using Google to find something but it all says ethier Dual-boot or the windows cd. Were using a flash drive to install the Windows OS.

I looked at microsoft's thing about removing Linux and it asks for a floppy disk, which well, it didn't come with and wouldn't have in the first place.

So is there any help for completely getting rid of Ubuntu and putting XP on the computer?

---

### Post by issih on 2009-03-01
If you can boot from the flash drive with the xp installer on it you should just get the option to format the drive as part of the install program, nothing else is necessary to wipe linux, just format the drive and install xp on it. You will need to adjust your bios to boot from usb ahead of the hard drive, but that should be all.

If for some reason this doesn't work you'll need to create a bootable linux usb thumb drive, boot from that and use the linux based partition editor (e.g. gparted) to format the hard drive, then install xp.

All this is assuming you have already tried using your ubuntu install and decided that it is not for you for some reason. If you haven't given it a fair crack of the whip yet then please do, have a play with it for a few weeks, it really is rather excellent ,and you just might like it.

Hope that helps

---

### Post by jey_xoxo on 2009-03-01
The installer won't start at all from the flash drive.
And we don't know how to create a Linux flash drive, and if you have to use a Linux computer to do that thats a loss for us because all the other computers we have run Vista and 1 has XP.

---

### Post by issih on 2009-03-01
You need to work out how to boot from the flash drive. Go into the bios and look for the option to change boot order. Make the usb drive be tried before the hard drive. I suspect you are in a situation where the system is set to try and boot from the hard drive first. Consequently it will just keep booting into linux regardless of whether you put the usb drive in the slot or not. You must tell the computer to look at the usb drive before the hard disk.

Hope that helps

---

### Post by yther on 2009-03-01
From some stuff I found by a quick search, it looks like you can press 0 when it's booting to choose which device to start from.  This is probably like pushing F12 on my Inspiron, a one-time choice that does not change any settings.

---

