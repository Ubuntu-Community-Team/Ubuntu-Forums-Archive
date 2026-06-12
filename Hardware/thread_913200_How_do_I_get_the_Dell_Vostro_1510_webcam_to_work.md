---
title: "How do I get the Dell Vostro 1510 webcam to work?"
date: 2008-09-07
forum: Hardware
---

### Post by riahc3 on 2008-09-07
How do I get the Dell Vostro 1510 webcam to work? Does anyone have expierences with laptop integrated webcams on Dells?

(The driver is from Creative it seems with oem14.inf being the inf file)

---

### Post by riahc3 on 2008-09-07
Anyone?

---

### Post by riahc3 on 2008-09-09
Bumping this thread up

---

### Post by riahc3 on 2008-09-14
Ive seen people with Dell laptops in these forums so someone has to have a solution.

---

### Post by JuryZ on 2008-09-17
Hello, I have this laptop and back on Arch Linux it worked well with the uvcvideo driver. However, I switched to OpenSUSE few days back and I can't get it to work again... Perhaps wrong build or just some fishy kernel setting. Please try it and refer what you find out. :)

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

---

### Post by riahc3 on 2008-09-29
> **JuryZ said:**
> Hello, I have this laptop and back on Arch Linux it worked well with the uvcvideo driver. However, I switched to OpenSUSE few days back and I can't get it to work again... Perhaps wrong build or just some fishy kernel setting. Please try it and refer what you find out. :)

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

On the same subject, is there a software that allows me to take pictures and/or record video (with audio) from my webcam?

---

### Post by sergiom99 on 2008-09-29
> **riahc3 said:**
> On the same subject, is there a software that allows me to take pictures and/or record video (with audio) from my webcam?

yes, try cheese
```
 sudo apt-get install cheese
```

and please post the output of 
```
lsusb
```

this will show your camera hardware driver as its detected by Ubuntu

---

### Post by tiosus on 2010-09-11
> **sergiom99 said:**
> yes, try cheese
```
 sudo apt-get install cheese
```and please post the output of 
```
lsusb
```this will show your camera hardware driver as its detected by Ubuntu

```
tiosus@tiosus-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

