---
title: "Need N-trig DuoSense Touchscreen and fingerprint scanner fully functional"
date: 2010-12-09
forum: Hardware
---

### Post by Enkouyami on 2010-12-09
Hi, I'm using Ubuntu 10.10 Desktop x64 on a HP TouchSmart tx2 notebook.

Here are some things my screen can do: Track my pen and left click by using my finger.

And here are some things I want it to do:
Left click using my pen
Support two finger inputs like right clicking using two fingers and resizing windows using two fingers

Theres also a few problems I have with my touchscreen.
Whenever I use my pen I am unable to left click using a mouse or my track-pad until I use my finger to left click.

When I ran this command:
```
cat /sys/bus/usb/devices/*/product
```
I got this:
```
USB2.0-CRW
HP Webcam
Fingerprint Sensor
DuoSense
EHCI Host Controller
EHCI Host Controller
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller
```

My fingerprint scanner is from DigitalPersona

Is there anything I could do to get these things?

---

### Post by Ayuthia on 2010-12-11
Welcome!  

EDIT: I removed the portion about changing the stylus to a left-click.  I mis-read the original message.

As for your fingerprint scanner, you can try the following [link]("http://ubuntuforums.org/showthread.php?t=760018").  I am not for sure if you will need aes2501-wy or not.  I will warn you that the last time I tried it out, the scanner still does not work too well in Linux.  It takes one snapshot of your fingerprint and then tries to match as many points as it can so it does not always get a good match.

For two finger gestures, it is not quite ready yet.  The packages to test out gestures is utouch (those should be in 10.10).  However, there is an application called [GINN]("https://launchpad.net/ginn") that is currently being worked on that will help "inject" gestures to applications.

For your pen/touchpad issue, are you currently up to date on changes?  Also, do you know what firmware version you are using for your touchscreen?  If you don't know, do you know whether you last used Windows 7 or Vista on the laptop?  Each firmware version acts a little differently in Linux.

---

