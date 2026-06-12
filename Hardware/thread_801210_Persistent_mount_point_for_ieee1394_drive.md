---
title: "Persistent mount point for ieee1394 drive?"
date: 2008-05-20
forum: Hardware
---

### Post by ultralame on 2008-05-20
I am trying to get my external drives to auto-mount in the same place each time, and I am having trouble getting them to work.  I am running Ubuntu 8.04, and they will need to automount so that non-su users can access them.

I would like them to mount in /media/pics and /media/vids.

The "pics" drive is an ieee1394 drive with one ext2 partition.  The vids drive is usb has one NTFS partition.

I have found a couple posts that say I should write a udev rule to get it to mount.  The problem is that I am not seeing the attributes that they suggest, and the ones that I try don't seem to work...

For example, they say, for the the ieee1394 drive, I should see SYSFS{guid}=XXXXXXX.  I don't.  I see ATTRS{guid}=XXXXX.  But this doesn't work when I substitute it in the udev rule.

Am I missing something?  Is there a better way to do this?  Can't seem to find a good article here that doesn't have the same problem.

---

