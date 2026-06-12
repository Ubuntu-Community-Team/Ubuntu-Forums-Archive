---
title: "Rejected transplant to new body"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by audrich on 2009-08-12
I installed Ubuntu 9.04 on an enclosed laptop HDD using a seperate device; I had to because the laptop it goes in cannot boot from external media.  Unfortunately now grub is still listing the host's OS (Windows XP) which is not there in addition to the installed Ubuntu.  There are a host of other minor glitches, particularly with GNOME, that I am guessing is rooted in this install method.  

What I'd like to know is, is there a way to repair grub and Ubuntu, for the OS to correct itself in terms of comforming to its new hardware environment (back inside the intended laptop)?  To me it feels like a case of a rejected organ transplant :confused:

---

### Post by bhaverkamp on 2009-08-12
LiveCD supports creating installer on a usb stick. This is how I install on my netbook.

---

### Post by audrich on 2009-08-12
> **bhaverkamp said:**
> LiveCD supports creating installer on a usb stick. This is how I install on my netbook.

The client machine does not support USB boot so that's not an option for me.  What would be nice is knowing what I need to transfer to a partition on that HDD in addition to the LiveCD contents to get it to start up installation on boot, basically making a recovery partition.  I've tried this by just copying over the LiveCD contents and it didn't start up.  Same story using a Windows i386 folder.  

I know I'm missing some sort of boot.ini or maybe autorun.inf but I'm clueless as to the details. 

 I've attempted PXE boots, but that method was a headache, especially since I can easily transfer files over through enclosure rather than FTP.

---

### Post by P4man on 2009-08-12
Maybe this can help:
[http://www.neowin.net/forum/lofiversion/index.php/t305843.html](http://www.neowin.net/forum/lofiversion/index.php/t305843.html)

there is a post there that describes how to use grub to boot a live cd ISO.
So you could make a partition on the laptop drive, just big enough to hold that. Insert the harddrive in the laptop, boot the "live cd" iso, install, then later remove the live cd partition to reclaim the disk space.

Not exactly a convenient way of doing stuff though :)

That said, the approach you followed should work too. If you got a bootable ubuntu now, then try reinstalling grub to clean it up:

```
sudo grub
root (hd0,0)
setup (hd0)
quit

```

---

### Post by audrich on 2009-08-12
> **P4man said:**
> Maybe this can help:
[http://www.neowin.net/forum/lofiversion/index.php/t305843.html](http://www.neowin.net/forum/lofiversion/index.php/t305843.html)

Looks good!  However I don't understand what I'm doing different than that except usea  different OS.  The CD image I got from the Ubuntu site has a boot launcher on it (isolinux), but when I start it up, I'm told "missing operating system, insert system disk when ready...".  It has all the necessary files to boot and install since I used the same files on a USB stick and that worked on a different computer that can boot from USB.  The only thing that differentiates the two has to be with the partition table or something.  ANy clues as to what I need to add or change to make what works on USB to work on HDD???

---

