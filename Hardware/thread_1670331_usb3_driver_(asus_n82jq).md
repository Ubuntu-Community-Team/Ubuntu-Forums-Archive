---
title: "usb3 driver? (asus n82jq)"
date: 2011-01-18
forum: Hardware
---

### Post by hamid_valad on 2011-01-18
hi every one
i am new with ubuntu, and I've got ubuntu 10.10 for my laptop. but i have problems with it. i appreciate help, step by step... (i apologise)
my laptop has a usb 3.0 port, my ubuntu finds the plug and uses it as a usb 2.0 plug. ( i got it because the copy pasting speed was very low)

is there any way to correct this?
(again, i am a beginner in ubuntu and linux, and thanks in advance)

---

### Post by hamid_valad on 2011-01-22
Any idea? :(

---

### Post by cascade9 on 2011-01-23
Using a USB 2.0 device on a 3.0 controller wont make the device any faster. ;)

---

### Post by hamid_valad on 2011-01-23
> **cascade9 said:**
> Using a USB 2.0 device on a 3.0 controller wont make the device any faster. ;)


i know that, i am using an external hdd witch is usb3. on windows its fast but in ubuntu its slow and the speed is for usb2... (sorry for my bad english)

---

### Post by cascade9 on 2011-01-24
What version of ubuntu are you using? USB 3.0 support came out with some of the newer kernels, if your kernel is too old you it will just use the USB 3.0 controller as USB 2.0.

---

### Post by hamid_valad on 2011-02-03
i am using ubuntu 10.10...

please help me, its very important...

---

### Post by hamid_valad on 2011-02-05
come on, nobody? any idea would be appreciated.. .

---

### Post by usercontrol on 2011-07-17
I have similar problem with Asus N43JQ. Ubuntu doesn't recognize any devices plugged into USB3 port. Dmesg says nothing.

lsusb:

```
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 014: ID 041e:30df Creative Technology, Ltd 
Bus 002 Device 005: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 004: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 003: ID 13d3:5122 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

