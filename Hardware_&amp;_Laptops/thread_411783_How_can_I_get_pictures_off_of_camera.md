---
title: "How can I get pictures off of camera"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by valkarin on 2007-04-17
I have an old Mustek mdc800 digital camera.  I don't have the money to get a new one.  I need to get the pictures from the camera to my computer.  The camera has a linux driver and i have it loaded.  I have mounted the camera.  The computer sees the camera.  Here is the output from lsusb

```
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 017: ID 055f:a800 Mustek Systems, Inc. MDC 800 Camera
Bus 002 Device 002: ID 8086:1120 Intel Corp.
Bus 002 Device 001: ID 0000:0000
```


Did I mention that the camera connects to the computer via USB?  On the second line the "Device 017" part increments every time I turn the camera on.  Would like to know what that means.  I also loaded the usb-storage driver after I couldn't get the pictures off the first time

The camera is not supported by gphoto2, gtkam, or gThumb image viewer.  I cannot access it like I would with a flash drive.  Please

**[SIZE="3"][COLOR="Red"]HELP[/COLOR][/SIZE]**

---

### Post by AndrewWalker on 2007-04-17
Just a guess but does your camera have an option for ptp transfer? If it has, make sure it is off and then the camera should appear as a standard memory stick.
As I said, just a guess but worth a try!

---

### Post by valkarin on 2007-04-17
Nope.  No PTP setting in the camera menu and no switch on the camera either.

---

