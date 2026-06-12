---
title: "Connecting a Nokia 770 web tablet with udev, hal, dbus, automount"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by Glennji on 2007-03-25
Hi all, I've got a Nokia 770 web-tablet and want to have a go at integrating it with Ubuntu a little better.  First of all I want to get it to mount to a known location.

I've written a udev rule so once plugged in I have a /dev/nokia770 device, which can be manually mounted to /media/nokia770.  But how do I automate this?

At the moment if I plug it in it is mounted to /media/usbdisk like any usb-drive.  That's great, but I really want a known mount point ... Any ideas where to look next?

---

### Post by s0cket on 2007-03-26
Sounds like all you need now is a HAL policy.  That or you can make an entry into /etc/fstab for it.  Before HAL checks its policy for an event it consults fstab.  If the device matches in fstab then it uses the mount point and ignores is own policy.

If you have to make a HAL policy god have mercy on your soul.  I've looked at the policy files and can't make heads or tails of them.  But I've never really took the time to try to understand them either.

---

