---
title: "ls* comand for PS/2 devices???"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by trethacker on 2008-01-04
I can't seem to find anything directly related to this issue so I turned here for some assistance. If this issue is already resolved and I am searching wrong or something, please let me know what or where to look.

I have a Netropa/Micro Innovations EZ-8000 Smart Office Keyboard that connects via PS\2.

It has the normal office/web/media keys but also has a scroller wheel on the left side as well as mark/cut/paste/ and some other speed keys that most office keyboards do not seem to have.

I found that the standard drivers for most of the office type keyboard drivers in Ubuntu will allow the media keys and some of the office keys to work, but I would like to have the full functionality of the keyboard if it is possible.

I was trying to find a command similar to lspci or lsusb that will show me connected devices on the ps/2 port so I could search the device address (eg: 0x0000:0x0000) and get an idea of what I can do to make it work, similar to looking up support for pci/usb devices with this method since they seem to be unique per each address depending on the device.

I can not seem to find an ls(ps2) type command to do this.

1) Is there a command of this nature for Linux/Ubuntu?

2) does anyone know if the full functionality of this keyboard is supportable in Linux/Ubuntu?

I dont believe it will matter but I am using 7.10 Gutsy Desktop Version.

The driver I am using now is one of the Microsoft Office/Internet keyboard drivers.

The actual disc that came with the keyboard is by Netropa but the disc does not have Linux support and the Netropa site no longer exists.

I dual boot into Windows and the features all work, so it is just a matter of getting these keys to work in Linux in order to be satisfied.

Thanks for any help in advance.

---

### Post by Yellow Pasque on 2008-01-04
I'm pretty sure you can get those keys working with the evdev driver (search for it)
Does this command give you what you want?
```
cat /proc/bus/input/devices
```

---

