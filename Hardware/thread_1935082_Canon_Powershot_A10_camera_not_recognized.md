---
title: "Canon Powershot A10 camera not recognized"
date: 2012-03-03
forum: Hardware
---

### Post by pwabrahams on 2012-03-03
I have a Canon Powershot A10 camera, but my Kubuntu 11.10 doesn't recognize it.  (I think it's recognized it in the past, though.)  lsusb sees it:
```
pwa@pwa-K60IJ:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5094 IMC Networks 
Bus 006 Device 010: ID 04a9:304f Canon, Inc. PowerShot A10
Bus 007 Device 002: ID 047d:1043 Kensington Ci65m Wireless Notebook Optical Mouse

```However, the Device Notifier says "No Devices Available".  Digikam can autodetect it but doesn't see anything on it -- the Import window is entirely empty.  (There definitely are pictures in the camera.)

What can I do to retrieve those pictures?

---

### Post by nd456 on 2012-03-04
I always use a card reader to avoid these types of issues. Plus it won't drain your battery for large transfers. As far as getting the physical camera to connect, that may be very tricky.

---

### Post by pwabrahams on 2012-03-04
I've discovered that there's a bug in gphoto2, #339563 at Launchpad, that causes this problem with a number of Canon cameras.  It's been confirmed but not fixed and dates back to 2009.  I'm wondering how the bug could have remained in that status for so long.

---

### Post by nd456 on 2012-03-05
> **pwabrahams said:**
> I've discovered that there's a bug in gphoto2, #339563 at Launchpad, that causes this problem with a number of Canon cameras.  It's been confirmed but not fixed and dates back to 2009.  I'm wondering how the bug could have remained in that status for so long.
Unfortionatly, there are more important bugs than a driver for a camera...

---

