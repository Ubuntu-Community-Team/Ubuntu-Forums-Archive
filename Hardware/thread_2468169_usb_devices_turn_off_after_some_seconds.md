---
title: "usb devices turn off after some seconds"
date: 2021-10-20
forum: Hardware
---

### Post by lukas34 on 2021-10-20
Hey,
When I'm plugging in a external usb drive, usb stick or any other usb storage device to my 18.04 machine, everything seems to work fine. Power LEDs flash until 3-5 seconds into the loading when they go out.
I cannot recognize any usb connection using  ```
lsusb
```.
Windows recognizes these devices on all ports. 
Other USB devices like webcams, mice, keyboards are detected on both OS.
Any idea on where I can start looking for solutions?
Lukas

/Edit: 
another weird thing I just found out is that when I plug in any non-storage device other than the ones that are working and that I mentioned (in this case a usb wlan adapter) and I run lsusb, the command takes about 20 seconds to execute compared to just a fraction of a second otherwise. Again it can't find anything

---

### Post by Autodave on 2021-10-20
What formatting is used on the unrecognized devices?

---

### Post by lukas34 on 2021-10-20
NTFS and some FAT but that shouldn't matter right? With my laptop (also running Ubuntu 18.04) all devices are detected. Also if my computer's Ubuntu would have some problems with NTFS drives, they should still be recognized as usb device even though mounting might be difficult.

---

