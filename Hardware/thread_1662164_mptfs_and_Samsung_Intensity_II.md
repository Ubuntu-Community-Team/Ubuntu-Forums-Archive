---
title: "mptfs and Samsung Intensity II"
date: 2011-01-07
forum: Hardware
---

### Post by LinuxNerdForLife on 2011-01-07
I have a Samsung Intensity II phone with a 16gb microSD card that I'm trying to access via usb on my laptop. I'm running 64 bit Ubuntu 10.04. I tried following the instructions for using mtpfs found here:
[http://www.anythingbutipod.com/forum/showthread.php?t=32817](http://www.anythingbutipod.com/forum/showthread.php?t=32817)
except I couldn't find the packages libmtp and mtptools, instead I installed libmtp8 and mtp-tools. When I run the command:
> sudo mtpfs -o allow_other /media/phone I can see the drive "phone" in nautilus but clicking on it gives the error:
> Error: Error stating file '/media/phone': Transport endpoint is not connected
Please select another viewer and try again.I can see the phone in the output of lsusb and I am in the FUSE member group.
I have the MTP plugin in Rhythmbox selected but cannot see the phone in Rhythmbox.

On the phone I go to Settings and Tools -> Tools -> USB Mass Storage.

I would like to be able to put music on my phone from my computer. Any help is much appreciated.

---

### Post by LinuxNerdForLife on 2011-01-10
Is this posted in the wrong spot? The problem persists.

---

