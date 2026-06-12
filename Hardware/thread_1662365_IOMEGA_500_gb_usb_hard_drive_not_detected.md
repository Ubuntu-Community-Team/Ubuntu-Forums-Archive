---
title: "IOMEGA 500 gb usb hard drive not detected"
date: 2011-01-08
forum: Hardware
---

### Post by Chake99 on 2011-01-08
running 32 bit kubuntu 8.10. I knwo it works on windows, but when I plug it in kubuntu I don't get anything in the devices recently plugged in tab. If I go under /dev/usb I find a hiddev0. Not sure if that has anything to do with it. My mouse is also plugged into USB right now.

Any sort of software I could get or commands I could use to resolve the problem?

Thanks in advance.

---

### Post by Fafler on 2011-01-08
dmesg | grep sd

This should give you info about the drives connected.
It likely a unclean ntfs filesystem. Install ntfsprogs or ntfstools or whatever its calles and run ntfsfix on the right devicename, similar to this:

ntfsfix /dev/sdb1

---

