---
title: "Simple Scan not working with Cannon LIDE110 in Ubuntu 14.04"
date: 2015-11-05
forum: Hardware
---

### Post by klrman on 2015-11-05
Simple-scan or Xsane or Gimp not working with my Cannon LIDE110 scanner. lsusb in shell displays scanner is detected, but that's about it. 
 Scanner does work in Win-7.  After reboot, Simple Scan detects scanner and crashed whilst trying to scan?

---

### Post by klrman on 2015-11-06
Anyone? :D

I can get it to scan, but after I close Simple Scan, or Xsane or Skanlite and then re-open the program, scanner is not detected anymore and the only way around this is
to physically remove the usb scanner cable and connect it again.  Scanner works fine in Win7.  I've been messing around with this for a couple of weeks and still can't
seem to get it to work.  Any ideas?  I'm quite new to Linux but want to give it a try.

I also should mention that the scanner is "not" detected when I first open my machine, so I need to boot, then pull the scanner usb cable and then re-connect again
for it to be detected.  Is there any way I can add the scanner somewhere so that my system will know about it permanently?


I have tried connecting the scanner cable to different usb ports and they are all 2.0.  Also tried a powered usb hub, but that didn't work either.

---

### Post by klrman on 2015-11-07
Just thinking about something. Anyone know a command I could type in the Linux terminal that would start the scanner?  Maybe something
to initialize it before I open the scanner software?  I noticed on my Win7 machine that when it boots, it also initializes my scanner and the 
scanner makes a few noises which must be windows way of making sure it is on.  When it is connected to my Linux machine and I boot,
nothing happens to the scanner and that could be where the issue is.

---

### Post by rolfkleef on 2015-12-01
I had similar problems that started when I got a new laptop: sometimes I could scan a page, mostly the scanner would abruptly stop and only a physical disconnect and restarting SimpleScan would maybe allow me to scan another page.

I found this on the libsane developer list: [http://lists.alioth.debian.org/pipermail/sane-devel/2015-October/034005.html](http://lists.alioth.debian.org/pipermail/sane-devel/2015-October/034005.html) with the answer that it might be due to timing problems in libsane. VueScan did work ok. So I took the suggestion to upgrade libsane.

With dependencies, I downloaded and installed these .deb files from a newer Ubuntu:

[http://packages.ubuntu.com/wily/libgphoto2-port12](http://packages.ubuntu.com/wily/libgphoto2-port12)
[http://packages.ubuntu.com/wily/libsane-common](http://packages.ubuntu.com/wily/libsane-common)
[http://packages.ubuntu.com/wily/libsane](http://packages.ubuntu.com/wily/libsane)

Seems to have fixed it on my machine.

---

