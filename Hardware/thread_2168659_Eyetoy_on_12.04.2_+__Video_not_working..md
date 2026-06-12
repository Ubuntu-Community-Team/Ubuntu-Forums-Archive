---
title: "Eyetoy on 12.04.2 + ? Video not working."
date: 2013-08-18
forum: Hardware
---

### Post by Merrattic on 2013-08-18
Eyetoy (black and silver) were working well on 12.04 32 bit, plug and play, but just upgraded my PC and went for 12.04.2 64 bit Xubuntu.

Detected in lsusb.

gspca_main / gspca_ov519 is loading and probing the device but then failing.

gspca not creating a /dev/video* device, so no Camera/Video. Seems things have taken a step back on 12.04.2 ?

Microphone detected and working in pulseaudio.

Looked into compiling ov51x-jpeg from sources but too much has changed since 2008 and it won't compile.

Some Outputs:
```
lsusb
#####
Bus 003 Device 004: ID 054c:0155 Sony Corp.


dmesg
#####
[    2.067268] gspca_main: v2.14.0 registered
[    2.067469] gspca_main: ov519-2.14.0 probing 054c:0155


[    9.283080] gspca_ov519: Can't determine sensor slave IDs
[    9.283088] ov519: probe of 3-10:1.0 failed with error -22
[    9.283118] usbcore: registered new interface driver ov519
[    9.285421] usbcore: registered new interface driver snd-usb-audio


hwinfo --usb
############
18: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: t1E6.Tjn4iaXZW80
  Parent ID: uIhY.2DFUsyrieMD
  SysFS ID: /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0
  SysFS BusID: 3-10:1.0
  Hardware Class: unknown
  Model: "Sony EyeToy USB camera Namtai"
  Hotplug: USB
  Vendor: usb 0x054c "Sony Corp."
  Device: usb 0x0155 "EyeToy USB camera Namtai"
  Revision: "1.00"
  Speed: 12 Mbps
  Module Alias: "usb:v054Cp0155d0100dc00dsc00dp00icFFisc00ip00"
  Driver Info #0:
    Driver Status: gspca_ov519 is active
    Driver Activation Cmd: "modprobe gspca_ov519"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (Hub)
```

Anyone had any success with this? Looks like this is now broken again after 12.04.1 LTS when it worked ?

Tried out on a variety of distros (mostly Debian based) with same kerenel level and same problem occurs. Worked fine with a boot CD of 12.04 LTS.

---

### Post by Merrattic on 2013-08-24
Anyone ?

---

### Post by Merrattic on 2013-08-25
Have now reported as a bug:

[https://bugs.launchpad.net/ubuntu/+bug/1216539](https://bugs.launchpad.net/ubuntu/+bug/1216539)

---

### Post by Merrattic on 2013-09-01
No-one know how to hack this thing ?

Just dug around in my "old things" bin and came up with an ancient Creative web cam. Plugged it in and dang if it doesn't need the same driver (what was ov51x-jpeg) :)

---

### Post by Merrattic on 2013-10-15
Resolved!
 Not a software bug as such, turned out to be the Intel xHCI mode  setting in the bios for USB for my Asus Z87M-PLUS motherboard. Default  setting was Smart Mode. This made all usb ports usb 3.0 and/or "better"  than 2.0, meaning my webcmas wouldn't play nicely. Changing the bios  setting to Disabled saw the camera fire up instantly, along with routine  connection of my DVB USB stick.
 Other option to try is Auto, and EHCI Hand Off to Enabled

---

