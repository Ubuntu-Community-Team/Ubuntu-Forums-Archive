---
title: "Palm? USB?"
date: 2004-11-15
forum: Hardware &amp; Laptops
---

### Post by mwillems on 2004-11-15
Hello all

OK, the usual Linux story - a day on somethign that should work out of the box, and no go yet... :-)

MY palm Tunsten|C  is not detected on this new box. It is plugged into a USB port. I have no /dev/ttyUSBx, but I do have /.dev/ttyUSBx whatever they are *I am used to RedHat, not Debian, sorry). USB must be working since the USB mouse works fine.

I have tried all the obvious stuff and made symlinks from /dev/pilot to "all of the above" - but still nothing. Help :-)

And after every reboot I get two "Gnome Pilot Initial Setup Windows"  now whether I like them or not. What a drag!

Can anyone help?

Michael

---

### Post by JProgrammer on 2004-11-15
Plug it in an push hot sync then

```
sudo tail /var/log/messages
```

There it should be detected and loaded my Tungsten E to /dev/ttyUSB1 and that worked. Too bad the backup module doesn't  :(

---

### Post by mwillems on 2004-11-15
[QUOTE=JProgrammer]Plug it in an push hot sync then

```
sudo tail /var/log/messages
```

There it should be detected and loaded my Tungsten E to /dev/ttyUSB1 and that worked. Too bad the backup module doesn't  :([/QUOTE]
 Nope, I have already tried that. When I plug and unplug, or push sync, nothing at all happens to /var/log/messages. As though it is not conencted (which it is) or as though usb is dead (which it is not - the mouse works). 

At my wit's end!

---

### Post by rkn on 2004-11-15
If the USB device is not detected Then try:
sudo modprobe usbserial
and
sudo modprobe visor

Then plug the device in and look for messages

and using 'tail' you might be missing something if there is lots of activity.
Look at the end of /var/log/messages.

---

### Post by TravisNewman on 2004-11-15
[http://howtos.linuxbroker.com/PalmOS-HOWTO.html#PC-CONNECT-USB](http://howtos.linuxbroker.com/PalmOS-HOWTO.html#PC-CONNECT-USB)
This page solved all my Palm vs. Linux headaches

---

