---
title: "External USB Hub problems"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by 6and9.42 on 2006-07-12
Hello,
First, thanks for all the help already! I've spent a good bit of time browsing the forums and have found solutions to most of the problems I've run into.

I'm pretty much a linux newbie, using Ubuntu for about a month. Anyway, USB problem, I'm using a Dell Inspiron 8200, it has 2 built in USB ports and I have a 4 port hub plugged into one of those ports. The ports on the computer work fine, but the hub does not. It shows up in Device Manager as "Unknown (0x1520)" and then has the following listed:

Unknown (0x1520)
- Jornada 548 / iPAQ HW6515 Pocket PC (I have a docking cradle & iPAQ hx4700 plugged into the hub)
- - USB Vendor Specific Interface
- - USB Raw Device Access
- USB Hub Interface
- USB Raw Device Access

Device Type, Capabilities, Device, and Vender are all "Unknown"

lsusb in the terminal gives this:

Bus 001 Device 009: ID 03f0:1016 Hewlett-Packard Jornada 548 / iPAQ HW6515 Pocket PC
Bus 001 Device 007: ID 04cc:1520 Philips Semiconductors
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 008: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000



If I plug my USB mouse into the hub it does not work, likewise with an external USB HD.

I'm not sure what to do next (OK, so I've not really done anything yet!) according to the device manager it's a Phililps hub (the hub itself is unmarked and several years old) but I was unable to find any informaiton about drivers, etc., on their website.

Is there a USB manager for Ubuntu somewhere?

Any tips would be great. Thanks.

g.

---

### Post by wadoryu on 2007-10-12
I have been reading through the forums and I too am having issues with my external usb hub. 

When I plug a device directly to my laptop's usb port it works (ipod, camera, external hd)
but when I use the usb hub, nothing works.

I am using ubuntu 7.04.

when i do a lsusb with my devices connected to the usb hub, this is what i get:

```
Bus 004 Device 009: ID 04a9:314f Canon, Inc. 
Bus 004 Device 007: ID 05ac:1205 Apple Computer, Inc. 
Bus 004 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 004 Device 002: ID 04fc:0c25 Sunplus Technology Co., Ltd 
Bus 004 Device 003: ID 05e3:0606 Genesys Logic, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  


```

any help would be appreciated.

---

### Post by wadoryu on 2007-10-13
bump

---

