---
title: "Usb ports doesn't work"
date: 2021-10-19
forum: Hardware
---

### Post by pad-0001 on 2021-10-19
Hi All
I installed in my hardware Ubuntu Server 20.04 to study something about. I notice that i can't see any device connected to usb ports.
To solve a previously issue, I went in bios to disable the USB 3.0, but in theory this "turned off" only the "blue ports".
If I perform lsusb command, the output is empty and trying to mount usb storage device, i can't see that in fdisk's output list.

Shomeone can help me to solve?


This is my first post in this forum.. Help me to improve me ;)

---

### Post by Autodave on 2021-10-19
What issue were you solving by turning off your USB3 ports?

Please give us some info on your system.

---

### Post by pad-0001 on 2021-10-20
The main issue was something like "usb *-*:device descriptor read/64, error -32" and I seen a lot of this during first tests to install.
The first time, i tried to go on but at the end, also during login, the output with the error was continuously.
Looking online, I found that usb 3.0 had to be disabled by bios, and this solved it.

I send you some info, tell me if you need more specific.

Motherboard:
Gigabyte Tech. Co.
970A-DS3P

Bios:
American Megatrends Inc.
F1
04/08/2013

---

### Post by Autodave on 2021-10-20
Would love to have the exact error code.  I have never heard of your particular problem.

---

### Post by pad-0001 on 2021-10-20
The issue was solve and this never appeared again. I can't retrieve the error but I wrote it down with a picture that i share you...

---

