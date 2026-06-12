---
title: "Help with USB hub and external disks"
date: 2008-05-06
forum: Hardware
---

### Post by cnbiz850 on 2008-05-06
I recently got a new USB hub.  It works with the mouse and printer, but not with external disks.  The disks don't even show up when I do "fdisk -l". I am using Dell Inspiron 6400 with Ubuntu 8.04.  The disks were formatted as EXT3.  They work well when I connect them directly to the computer.  I search the forum and it seems no related topics.  Does anyone know what is going on?

---

### Post by prshah on 2008-05-06
> **cnbiz850 said:**
> I recently got a new USB hub.  It works with the mouse and printer, but not with external disks.  The disks don't even show up when I do "fdisk -l". I am using Dell Inspiron 6400 with Ubuntu 8.04.  The disks were formatted as EXT3.  They work well when I connect them directly to the computer.  I search the forum and it seems no related topics.  Does anyone know what is going on?

Is the hub powered externally, or does it run off the computer's usb power? In many cases, the computer/laptop usb port cannot supply enough power to hubs for devices such as usb drives, etc. In such cases, you need to have external power to the hub, or, if your drive has a Y cable, connect one end to TWO ports and the other to the drive. This too may not work if your hub cannot handle the power load.

---

### Post by cnbiz850 on 2008-05-06
Thanks very much for the reply.  My hub is not externally powered, so it could be the problem.  I guess the best way is to get a powered hub then?

---

