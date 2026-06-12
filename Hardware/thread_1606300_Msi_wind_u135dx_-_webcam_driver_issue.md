---
title: "Msi wind u135dx - webcam driver issue"
date: 2010-10-26
forum: Hardware
---

### Post by youbuntu on 2010-10-26
Hi. I have an MSI U135DX, the updated revision of the U135. The webcam can be seen toggling on/off when I do "lsusb", when I press Fn+F6 (webcam key combo).

I'm running Ubuntu 10.10 i386.
Neither Cheese nor Guvcview see the camera. Here is the output from lsusb:

```
Bus 001 Device 002: ID 5986:0314 Acer, Inc 

```If someone could help, I'd be so happy :D

Thank you all

---

### Post by jaesjg on 2010-10-26
I'm having a similar problem on my compaq CQ 40 laptop whose integrated webcam isn't even being detected. Cheese crashes on starting, and lsusb shows:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 19d2:fffe ONDA Communication S.p.A. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I've tried reinstalling the gstreamer ugly and bad libraries  to no effect.

HELP!

---

### Post by janneknower on 2011-02-18
Hi,

I have installed lubuntu 10.10 to my U135DX and the web camera is working. Try to use it with Skype (Options->Video Devices->Test) after enabling it (Fn-F6) and seeing it with lsusb command.

"Cheese" does not seem to work, dunno why. Write me if you want more information, and good luck!

---

