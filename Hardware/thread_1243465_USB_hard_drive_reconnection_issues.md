---
title: "USB hard drive reconnection issues"
date: 2009-08-18
forum: Hardware
---

### Post by hellfeuer on 2009-08-18
I have a Seagate 500 gb external usb hard drive. It has a seperate power source (i.e. does not draw power through usb). A couple of times I accidently pulled at the power cord so the drive powered off and on briefly. The problem is this:

If I turn off power to the drive while the drive is mounted, and then turn the power on, Ubuntu does not remount the partitions on the hard drive until I restart, so I have to do it manually, with mount.
gnome-mount -v fails with the error:
** Message: Given device '/dev/sdc1' is not a volume or a drive.
mount works just fine. And on restarting, everything is back to normal.

Also, after this power thing has happened, Ubuntu won't even restart properly. The progress bar on the shutdown screen 'unloads' completely and then nothing happens, so I have to do a hard reset. 

How do I fix this?
Thanks

---

