---
title: "Feisty USB device msg: Could not claim device"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by infrared on 2007-07-25
I have a usb device (Ocean Optics HR4000) that worked in Breezy, but shows the following error when I start the vendors software using Feisty (clean install):
          Opening interface 0
          Could not claim device (Vid: 0x2457, Pid: 0x1012, iface: 0)

If I open the vendor software using 'sudo', then the software runs as it should (just like it did in Breezy without using sudo).

I have attempted a few fixes (none of which have worked):
1) edit /etc/udev/rules.d/ and restart udev as described here:
[http://ubuntuforums.org/showthread.php?t=346840](http://ubuntuforums.org/showthread.php?t=346840)
and here:
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146)
2) recompiled the kernel ensuring that CONFIG_USB_SUSPEND is not defined as described here:
[http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html)
The above page also describes a method of editing /etc/udev/rules.d/.  This method didn't work either.

I've tried a number of other things.  Most of them are similar to item 1 above and are all aimed at digital cameras and libgphoto.

Is this a device permissions issue?  What should I do next?

Thanks for the help.

- infrared

---

