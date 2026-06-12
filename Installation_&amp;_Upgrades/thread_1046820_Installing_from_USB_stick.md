---
title: "Installing from USB stick"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by Featherstone-Hough on 2009-01-21
Greetings, all.  I'm trying to install 8.04LTS on a rackmount server that has no CDROM and no floppy drive, so I have elected to do the installation from a USB stick.  I have followed the instructions here:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

using UNetbootin to prepare the USB stick from an ISO image.  No troubles so far, and the machine boots into the installer just fine.

The problem is when the installer gets to the "detect CD" stage.  It of course doesn't detect a CDROM drive (since there isn't one) and won't accept "none" etc under the branch to manually detect the CDROM...  The installer seemingly will not proceed past this point if no CDROM device is detected/specified...  It just won't take "no" for an answer!  ;-)

How can I get around this?  Does the installer *require* a CDROM for some reason, even when it's not running from one?  Is there a workaround, and/or am I missing something?  I suppose the installer doesn't necessarily know it's not running from a CD, but why does it insist on a CD drive being present?

Any insights would be gladly welcomed.

---

### Post by SkyLeach on 2009-01-21
> **Featherstone-Hough said:**
> Greetings, all.  I'm trying to install 8.04LTS on a rackmount server that has no CDROM and no floppy drive, so I have elected to do the installation from a USB stick.  I have followed the instructions here:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

using UNetbootin to prepare the USB stick from an ISO image.  No troubles so far, and the machine boots into the installer just fine.

The problem is when the installer gets to the "detect CD" stage.  It of course doesn't detect a CDROM drive (since there isn't one) and won't accept "none" etc under the branch to manually detect the CDROM...  The installer seemingly will not proceed past this point if no CDROM device is detected/specified...  It just won't take "no" for an answer!  ;-)

How can I get around this?  Does the installer *require* a CDROM for some reason, even when it's not running from one?  Is there a workaround, and/or am I missing something?  I suppose the installer doesn't necessarily know it's not running from a CD, but why does it insist on a CD drive being present?

Any insights would be gladly welcomed.

It needs to know where to find the files.  I have not tried this, but attempt the following:

press ctrl+alt+f2 to switch to an alternate terminal and then do 'ls -alh /mnt' to see the name that automount gave the usb key.  I suspect it will be something like /mnt/usbkey but I can't be certain since I have not actually done this.

At any rate, when you know where the usb is mounted do the following:

mount -o bind /mnt/usbkey /mnt/cdrom

then give /mnt/cdrom as the location of the install cd.

I hope this helps.  :-)

---

### Post by Featherstone-Hough on 2009-01-22
Thanks for the reply.  Alas, your suggestion didn't quite work...  Looking for the USB key in the /mnt directory results in a great big nothing:

```
# ls -alh /mnt
drwxr-xr-x  2 root root     0 2009-01-22 09:30 .
drwxr-xr-x 14 root root     0 2009-01-22 09:30 ..

```

I also tried looking at /dev/sd* , and a /dev/sdb1 exists which I figured could be the USB key, but I was unable to mount it in /mnt .  Also, /media doesn't exist, I tried that too.

Any other ideas?  :-)  Your basic idea that the installer needs to be shown where the files are sounds right (although I think it's a little odd that it doesn't know what device it's running from), but the particulars of how to do that aren't necessarily obvious to me.

---

