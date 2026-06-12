---
title: "run command on mount/umount without interfering with automount"
date: 2008-11-16
forum: Hardware
---

### Post by SqRt7744 on 2008-11-16
Hi I have a Western Digital Passport 250 GB USB drive (1058:0702 Western Digital Technologies, Inc. Passport External HDD). I haven't been able to use it reliably since I originally purchased it a year ago (loss of data, slow transfers, etc)

I have finally traced down the problem and can now use the drive. After connecting it I have to run (as root, and assuming it has been assigned to sdb)
echo 64 >/sys/block/sdb/device/max_sectors

and finally after unmounting the drive, I have to run 
sdparm --command=stop /dev/sdb.
before disconnecting it.

Now I am trying to figure out how to have this happen automatically when I mount/unmout the drive, and preferrably be integrated with gnome's (nautilus) eject system so that my girlfriend doesn't have to resort to the command line.

I've been trying various things with udev and hal but can't really figure it out - at least not without nautilus complaining that it can't eject the volume when I try.

Does anyone have an idea how to get this to work?

thanks

---

### Post by Elfantin on 2009-01-12
Hi, you say you've tried udev. I wonder if you've tried this?

I've created a rule {/etc/udev/rules.d/62-MikMountFlash.rules} like this:

ACTION=="add|remove",ENV{ID_FS_UUID}=="C840-61F5",PROGRAM="/home/mik/bin/provausdev.sh"

When I plug in or remove the flash drive, the named script gets executed. This actually targets a precise partition on the disk, as that is my goal. I believe you can equally well target the whole disk using ID_SERIAL, rather than the ID of the fs. One thing is that you need to be careful as to how you number your script (I started putting it as 50-.rules but it didn't work as, I guess, the ENV is set by another rule). 
Also, you can get info about your device by running:
sudo udevadm monitor --environment
before inserting/removing it.

I can't really say if it complains when un-mount, as mine has been doing the complaint business for some time, BEFORE I touched anything in udev :)

Hope it helps.

PS. Forgot to say that the environment is available to the program, so for example my test script is like this:

#!/bin/bash
echo The device: >> /home/mik/temp/usbdevtest
echo ID_VENDOR=$ID_VENDOR >> /home/mik/temp/usbdevtest
echo has been $ACTION(e)d on >> /home/mik/temp/usbdevtest
date >>/home/mik/temp/usbdevtest

with a simple case structure you can perform different actions on add/remove.

---

### Post by SqRt7744 on 2009-01-18
thanks, but one more question, when I unmount the drive, will udev call the script? That's the most important thing for me I suppose. It isn't much use if the 'remove' action is first called once I've physically pulled the usb cable from the computer....

---

