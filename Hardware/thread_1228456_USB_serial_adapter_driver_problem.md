---
title: "USB serial adapter driver problem"
date: 2009-07-31
forum: Hardware
---

### Post by fredyu on 2009-07-31
Hi!

I am new to the ubuntu community and I have trouble figuring out what the ubuntu manual actually says....... :(
I was trying to use a Cyberpower usb-to-serial adapter. It is an old model and so there's no driver support from its manufacturer. Ubuntu recognized the adapter at /dev/usb/hiddev0 (as opposed to what I hope would be /dev/ttyUSB0), but then Minicom said "Cannot open /dev/usb/hiddev0". When I headed back and checked hiddev0's presence, it's gone. I did some googling and thought it was probably the problem of the driver. I found the following manual and thought I saw the light at the end of the tunnel. I failed.

> **INSTALLATION**

        This  driver  is not built by default.  You can build it by using "con-
        figure --with-usb=yes". Note  that  it  will  also  install  other  USB
        drivers.
 
        You  also  need to install manually the legacy hotplug files (libhidups
        and libhid.usermap, generally in /etc/hotplug/usb/), or the  udev  file
        (nut-usbups.rules,  generally in /etc/udev/rules.d/)to address the per-
        mission settings problem. For more information,  refer  to  the  README
        file in nut/scripts/hotplug or nut/scripts/udev.
 
        On  Linux  with MGE equipment, you will need at least a 2.4.25 or 2.6.2
        kernel as well as libusb-0.1.8 or later to disable hiddev  support  and
        avoid conflict.Quoted from [http://manpages.ubuntu.com/manpages/karmic/man8/usbhid-ups.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/usbhid-ups.8.html)

[FONT=Verdana]Where am I supposed to "configure --with-usb=yes"? like in which folder or file? I can't find the folders/files in the quote.[/FONT] [FONT=Verdana]What EXACTLY am I supposed to do? Thanks in advance! [/FONT]

---

