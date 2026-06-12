---
title: "Card reader is not recognized"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by niethslim on 2007-12-31
I've bought a new camera and I've got a usb card reader with it.
Ubuntu doesn't recognize the card reader, it has no reaction at all to it.
I don't know the brand/model of the CR but it can't be expansive if it came with the camera.
Is there any software that can deal with it, or any other way to make it work?

Thanks in advance,

---

### Post by jarthurs on 2007-12-31
Firstly from the command line without the card reader inserted type *lsusb* now plug it in and type *lsusb* again. Hopefully you should see a difference in the form of a 'mass storage device' of some description, some card readers don't give much of a response without a card inserted. I have a cheap SD card reader which only seems to go live once a card is inserted.

All the readers I have access to appear and mount cards automatically under Ubuntu Gutsy.

This should give you an idea if your reader is being seen at a hardware level, even if the card is failing to mount.

Regards,
Jason.

---

### Post by niethslim on 2007-12-31
Thanks for the quick reply, jarthurs.
The output of lsusb with the card reader inserted is: 
```
Bus 002 Device 022: ID 090c:6000 Feiya Technology Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```
The  "Feiya Technology Corp. " thing is the card reader.
It is recognized with or without the card, however the indicator light of the card reader is only on with a card inserted.
Any idea how can i access the card reader?

---

### Post by niethslim on 2008-01-01
Bump

---

### Post by niethslim on 2008-01-01
Nobody has a solution?:confused:

---

### Post by elbono on 2008-01-01
I have the same problem, Every once in a while the reader stops mounting the SD card after it is inserted.

When i run lsusb the output is:

```
eoin@AlwaysCamping:~$ lsusb
Bus 004 Device 002: ID 058f:6362 Alcor Micro Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

can anyone give us a suggestion?

---

### Post by orbister on 2008-03-13
> **niethslim said:**
> Thanks for the quick reply, jarthurs.
The output of lsusb with the card reader inserted is: 
```
Bus 002 Device 022: ID 090c:6000 Feiya Technology Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```
The  "Feiya Technology Corp. " thing is the card reader.
I've got one of them. It's useless with Ubuntu on my Netvista: mounts OK, but copies images unfeasibly fast - by losing lots of data on the way. Works fine with XP and with an ASUS WL-HDD2.5, which runs a version of Linux.

---

