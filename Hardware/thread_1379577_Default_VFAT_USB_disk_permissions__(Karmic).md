---
title: "Default VFAT USB disk permissions?  (Karmic)"
date: 2010-01-12
forum: Hardware
---

### Post by kruegerc on 2010-01-12
Hey guys,

I've noticed that in Karmic (9.10) the default vfat umask has changed to 022 (resulting in 755 permissions when a user mounts a USB external disk).  This is well and good, however, I'd like to know how to manage these permissions.

In past versions, gnome-volume-manager was the default, with which gconf-util could be used to manage the default umask.  This no longer seems to be the case...  Could someone point me in the right direction?

And yes, I know I can statically mount it as I want via mount, adding an entry in my fstab, and so forth.  I want to define the default umask appled to vfat disks when automounted as the running user.

Thanks in advance!

Campbell

---

### Post by kruegerc on 2010-01-14
Really...?  Nothing?

I've found that Nautilus is now responsible for disk mounting (superseding gnome-volume-manager), but can't seem to find a damn bit of information regarding how to configure it.

Any tips?  At all?

---

### Post by nomnex on 2010-01-14
kruegerc, I have been asking on #ubuntu and several other IRC channels about the change for auto-mounted USB devices in /media on Karmic vs. Jaunty. I did find anything on the Karmic release page either. I subscribe to the thread.

---

### Post by Sirion on 2010-01-17
I have the same problem. 

Karmic broke a few things for me that are really annoying (like authorizations, filesystem premissions, all uppercase labels for my usb-sticks...)  and I cannot find any information on how the new system works. Is there some central document that describes all changes with a bit more detail than "we change id."?

---

