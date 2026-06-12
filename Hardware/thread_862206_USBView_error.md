---
title: "USBView error"
date: 2008-07-17
forum: Hardware
---

### Post by groundnut on 2008-07-17
I have installed USBView on my Xubuntu Hardy Heron computer.
However after the command usbview I get the following error:

USBView error.

Can not open the file /proc/bus/usb/devices

Verify that you have USB compiled into your kernel, have the USB core modules loaded, and have the usbdevfs filesystem mounted.

So what do I have to do to get it work?

---

### Post by brian.takita on 2008-07-30
Hello, I'm also getting this exact issue. Any help would be appreciated.

Thanks,
Brian

---

### Post by lostdave on 2008-07-30
from the Following List Posting
[https://lists.ubuntu.com/archives/ubuntu-users/2008-June/148307.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-June/148307.html)

Make sure you have usbfs mounted, which can be found in	/etc/fstab, by adding the following line:
```

 # <file system> <mount point>   <type>  <options>
 none            /proc/bus/usb   usbfs   defaults

```

Then 'mount -a' to make sure its mounted. You should now have a /proc/bus/usb directory heirarchy. The "new" udev and libusb will be using /dev/bus/usb, but many	applications still use /proc/bus/usb, so we'll mount it until that gets deprecated.

---

### Post by cariboo on 2008-07-30
It won't work because the file it is pointing to does not exist. You can get the same result by opening an terminal and typing:

```
lsusb
```

Jim

---

### Post by lostdave on 2008-07-30
I Beg to differ, but the solution posted does work...
but yes...same result at a command line...no disputing that :-)

Dave

---

### Post by faheyd on 2009-04-24
> **lostdave said:**
> I Beg to differ, but the solution posted does work...
but yes...same result at a command line...no disputing that :-)

Dave

This is still broken in Intrepid, and this solution still works.

Thank you for the help.  When will things like this EVER get fixed.

---

