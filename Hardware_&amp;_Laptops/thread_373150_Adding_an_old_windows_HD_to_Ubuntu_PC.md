---
title: "Adding an old windows HD to Ubuntu PC"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by karishbhr on 2007-03-01
One of my old computers just died. In it was a 160 HD that I want to add to my linux setup.  The HD had been for windows xp.

How do I format the HD on my ubuntu PC and get it running as an extra HD on that setup?

---

### Post by jethro10 on 2007-03-01
Basically install gparted from synaptic.

This will see the new disk and let you format it, see how it is named etc.

Then you create a mount point (a folder effectivley) where you want the disk to appear in your filesystem.

You can mount it from a command line manually to test it all, but this will be lost every re-boot.
So then you put an entry in /etc/fstab/ to mount the disk in its new place on startup.

this may help
[http://www.ubuntux.org/edit-fstab-to-mount-partition-at-startup](http://www.ubuntux.org/edit-fstab-to-mount-partition-at-startup)
or this
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)   This one has pictures of gparted running, not it shows you the "name" of your new disk which will probably be something like /dev/hda4

J

---

