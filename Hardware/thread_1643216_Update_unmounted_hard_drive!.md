---
title: "Update unmounted hard drive!"
date: 2010-12-11
forum: Hardware
---

### Post by Enyo88 on 2010-12-11
I have a dual boot laptop, with vista and ubuntu 10.04, and about a week ago i was using ubuntu while it was performing updates.  After the updates were complete and i restarted my computer, the BIOS could not find the Vista partition, and with the ubuntu partition, it can find it, but when i tried to load it, it can not find the drive in dev/disk/by-uuid.  I have ubuntu on a flash drive and i'm able to start my computer and use that, and am able to access the files on the ubuntu partition, but not the vista partition. I have tried mounting both of them, but am unable to. Please help!!

---

### Post by dandnsmith on 2010-12-11
I'm slightly confused here - the BIOS has nothing to do with partitions as such, all it is concerned with is getting to the primitive bootloader on the HDD, which tells it what to do next.

One thing you could try is to start gparted from the USB OS, and see what that makes of the hard disk - it could be that the update has done some mischief with the booting or the partition table (but I think the latter unlikely).

Did you mean that you ran blkid from the USB?

---

### Post by Enyo88 on 2010-12-11
i'm kind of new, so sorry for the confusing description! but thanks for your help!!! :)

---

### Post by Enyo88 on 2010-12-11
I reinstalled Ubuntu, and it seems to be working (for now), is there any way I could mount my vista partition from here for it to be accessable again from the boot menu?

---

### Post by dandnsmith on 2010-12-12
There is no connection between mounting it inside Ubuntu, so you can see the content, and having Windows bootable from the boot menu.

If it isn't there as a boot option, then the bootloader hasn't been properly configured. I think you need to do a grub-update to get it to rescan the OSs installed, but am no expert on grub2.

I suggest doing a forum search on *grub-install* and *grub-update* to find threads where this is discussed - you may also need to run the script to show what boot options and loaders are installed on your system, so you can post the results for consideration.

BootInfo Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

