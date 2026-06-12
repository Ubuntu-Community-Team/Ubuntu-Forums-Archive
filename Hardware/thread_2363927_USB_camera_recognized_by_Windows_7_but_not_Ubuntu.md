---
title: "USB camera recognized by Windows 7 but not Ubuntu"
date: 2017-06-16
forum: Hardware
---

### Post by archaeometrist on 2017-06-16
I have a real headache... I'm trying to get an older USB camera (Tucsen 1.3mp microscope camera) working so I can do some stuff at home.  The problem is, when I use an old laptop (W7) it recognizes the USB is present and returns the proper ID information, but on my main computer (Ubuntu 14.04LTS), the USB doesn't register as ever being connected.  Using lsusb and sudo lsusb, the camera doesn't show up.  Dmesg also doesn't show any new changes when the camera is plugged in.  Any other device shows up, and works.  All of the USB ports on my computer work no problem.  I can plug anything else (RTL-SDR, Flash drive, backup drive, whatever) in and they're recognized.  I HAVE had problems in the past with webcams not working right... I have one (rarely used and not plugged in) that works now.  I've also tried this camera in the past and had problems with it... it was recognized but Cheese and other programs wouldn't pick up the picture.  Any suggestions as to where to look?  I'm not a newbie but also not a "guru" when it comes to Ubuntu and I'm stumped.

---

### Post by efflandt on 2017-06-16
Unless the camera only has internal memory or is so old that it used a Smart Card (which was just the opposite of smart), if it uses SD/microSD have you tried putting that in a USB card reader? That should work unless the camera uses unusual formatting or file type.

---

### Post by archaeometrist on 2017-06-16
The camera doesn't have either.  It's much like a webcam, except made for use with a microscope (different optics, mounting, etc.).  I have a digital camera that can be adapted to a microscope, but it poses a whole new set of problems that I'd rather not mess with.  With the present system, once I get it working I can measure (with some accuracy) the microscopic things I take pictures of.

---

