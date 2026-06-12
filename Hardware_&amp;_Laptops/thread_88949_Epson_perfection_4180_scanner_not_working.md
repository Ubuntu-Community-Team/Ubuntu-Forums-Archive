---
title: "Epson perfection 4180 scanner not working"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by greenpenguin on 2005-11-11
I've got and epson perfection 4180 flatbed scanner, which does not want to work with ubuntu.
When I tried running xsane, it would crash when i clicked scan (i think it was looking at my tv card).  I modified /etc/sane.d/epson.conf and added ```
usb 0x04b8 0x0118
``` to the end.  Now sane lets me select epson flat bed, but when i click scan i get "Failed to start scanner: invalid argument".

I have also tried using iscan.  This says "could not send command to scanner.  Check the scanner's status."

I could really do with some help here - im lost :(

---

### Post by Teroedni on 2005-11-11
You need Epson driver here
[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

---

### Post by greenpenguin on 2005-11-12
I've tried this driver, but i sill cant get it to work

---

### Post by Teroedni on 2005-11-13
Are you using epson software too?
I think youy need to use only Epson softyware in order to get it work
Also could you check in /var/log for an log file whiuch may tell you what went wrong?

---

### Post by greenpenguin on 2005-11-14
Using xsane and libsane extras:
/var/log/syslog:

```
Nov 14 19:22:35 localhost python: hpssd [WARN] Inrecognized URI: usb://Canon/iP4000
Nov 14 19:22:35 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport0: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:22:35 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport1: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:22:35 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport2: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:22:35 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport3: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:22:37 localhost kernel: [4295411.790000] usb 3-3: usbfs: interface 0 claimed while 'xsane' sets config #1
Nov 14 19:22:39 localhost kernel: [4295413.332000] usb 3-3: usbfs: interface 0 claimed while 'xsane' sets config #1

``` 
With iscan when package iscan installed:
/var/log/syslog:
```
Nov 14 19:27:48 localhost python: hpssd [WARN] Inrecognized URI: usb://Canon/iP4000
Nov 14 19:27:48 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport0: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:27:48 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport1: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:27:48 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport2: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:27:48 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport3: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:28:15 localhost python: hpssd [WARN] Inrecognized URI: usb://Canon/iP4000
Nov 14 19:28:15 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport0: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:28:15 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport1: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:28:15 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport2: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:28:15 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport3: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:28:15 localhost kernel: [4295749.322000] usb 3-3: usbfs: interface 0 claimed while 'iscan' sets config #1
``` 
And xsane with neither installed:
/var/log/syslog:
```
Nov 14 19:31:02 localhost python: hpssd [WARN] Inrecognized URI: usb://Canon/iP4000
Nov 14 19:31:02 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport0: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:31:02 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport1: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:31:02 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport2: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov 14 19:31:02 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport3: No such file or directory: io/hpiod/ppdevice.cpp 827 
``` 
There look slightly similar to me, so i think the problems are linked...

Anyone?  Oh, and this is Ubuntu 5.04.

---

### Post by Teroedni on 2005-11-15
This seem very wrong.
Could you try to completely remove xsane and everythig else you have installed.?And than Install xsane and the Epson package?

---

