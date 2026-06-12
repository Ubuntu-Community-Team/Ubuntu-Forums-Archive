---
title: "Connecting UPS serial to USB"
date: 2010-05-01
forum: Hardware
---

### Post by TJ6900 on 2010-05-01
Hello,

I have a Liebert UPStation GXT which has a serial connection that I wont to hook to my Ubuntu workstation using either powstatd or nut programs. The problem is my motherboard doesn't have an onboard serial connection, but I do have a serial to usb converter. Now once the serial to usb is all connected properly, I have no idea where in /dev it would be, I know normal serial connections are added in /dev/ttyS0. Powstatd of coarse doesn't respond to anything when set to watch on ttyS0 or ttyS1... etc.

Is there any idea where this Serial to USB connection is placed in /dev? Or what way or log can I view to troubleshoot this problem?

---

### Post by ecerutti on 2011-01-04
try with /dev/ttyUSB0

---

