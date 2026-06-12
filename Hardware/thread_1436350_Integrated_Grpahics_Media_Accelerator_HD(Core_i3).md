---
title: "Integrated Grpahics Media Accelerator HD(Core i3)"
date: 2010-03-22
forum: Hardware
---

### Post by shaunkerr on 2010-03-22
I just installed Ubuntu 9.10 last night and noticed that it didn't pick up my graphics drivers and just displays at 1024x768 (In windows it's 1366x768 ). My question is how do I fix it, if that's possible?:confused:
 
 
Ubuntu 9.10 x64
Adapter Type: Intel Graphics Media Accelerator
Chip Type: Intel Graphics Media Acclerarator HD (Core i3)
 
Laptop Asus U50F

---

### Post by ajgreeny on 2010-03-22
Try **System ->Administration ->Hardware Drivers**.  Normally this is offered automatically when the system is booted, but perhaps yours is not yet online.

---

### Post by shaunkerr on 2010-03-22
Ok, well I checked it and it says there are no proprietary drivers so everything in the boxes are empty/blank.

Shaun

---

### Post by gordintoronto on 2010-03-22
The on-board graphics in the I3 are not supported yet. To get the higher resolution display, follow the directions in this thread:
[http://ubuntuforums.org/showthread.php?t=1425547&highlight=nomodeset+intel](http://ubuntuforums.org/showthread.php?t=1425547&highlight=nomodeset+intel)

---

### Post by shaunkerr on 2010-03-22
> **gordintoronto said:**
> The on-board graphics in the I3 are not supported yet. To get the higher resolution display, follow the directions in this thread:
[http://ubuntuforums.org/showthread.php?t=1425547&highlight=nomodeset+intel](http://ubuntuforums.org/showthread.php?t=1425547&highlight=nomodeset+intel)


I tried to add the nomodeset during startup, but when I went to change the resolution it was still 1024x768.  Is anything else I can try?

---

### Post by gordintoronto on 2010-03-24
> **shaunkerr said:**
> I tried to add the nomodeset during startup, but when I went to change the resolution it was still 1024x768.  Is anything else I can try?

Son of a gun. My only thought is pretty silly: look for a cheap nVidia video card on eBay to tide you over until the driver for the i3 appears. (My wife's computer uses a video card which cost me the princely sum of $10. Canadian.)

---

### Post by jocko on 2010-03-24
> **gordintoronto said:**
> Son of a gun. My only thought is pretty silly: look for a cheap nVidia video card on eBay to tide you over until the driver for the i3 appears. (My wife's computer uses a video card which cost me the princely sum of $10. Canadian.)
Isn't even a cheap nvidia card going to be better than the integrated graphics of the i3 anyway?

---

