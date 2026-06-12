---
title: "Vuescan on Edgy - permission problem"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by jeffbarish on 2006-10-30
I just switched to Edgy from another distro.  I am having trouble getting Vuescan to work correctly.  It runs fine with sudo, but otherwise I get a message that it found the scanner (Epson Perfection 3170) but no Epson software.  If I cat /proc/bus/usb/devices, I see the Epson scanner but for driver it says (none).  If I run Vuescan with sudo, then the driver is usbfs.  Clearly all the software I need is here, so there must be a permissions problem.  I found a description at [http://www.freecolormanagement.com/sane/libusb.html](http://www.freecolormanagement.com/sane/libusb.html) of what one is supposed to do to correct a permissions problem.  The first step is to modify a file in /etc/hotplug.  The procedure worked fine on the previous distro, but Ubuntu does not seem to have /etc/hotplug.  Does anyone know what I am supposed to do instead?

---

### Post by jeffbarish on 2006-10-31
Maybe I should have asked this question differently.  What I really want to know is what does Ubuntu use instead of hotplug?  My previous distro had /etc/hotplug but Ubuntu doesn't, so either Debian has evolved or Ubuntu is doing something unusual.  In either case, the key to solving my problem is to figure out how Ubuntu associates a driver with a pluggable USB device.

---

### Post by marvinthesad on 2006-11-09
You might want to check: [http://www.ubuntuforums.org/showthread.php?t=11718](http://www.ubuntuforums.org/showthread.php?t=11718)

udev is the new system, tools:
$ lsusb
$ sane-find-scanner
(root) $ scanimage -L
(non-root) $ scanimage -L

---

