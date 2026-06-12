---
title: "HP Pavillion dv9000 Ricoh web cam"
date: 2008-08-14
forum: Hardware
---

### Post by koolguynet on 2008-08-14
I have tried following the instructions I can find, but can't get the web cam on my dv9000 working.  I am using Hardy 64-bit version.  What information would be useful to help me get this working?

---

### Post by sergiom99 on 2008-08-14
post the output of this command:
lsusb

You'll find there the hard-specs of your cam to search the forums for specific solutions.

Also, which program are you trying your cam with? cheese? IM apps?

---

### Post by cdtech on 2008-08-14
I use "cheese" for my web cam. This will let you know your web cam is working as well.
```
sudo apt-get install cheese
```

P.S.
"lsusb" does show you what is connected via usb and will probably show something like this:
```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 001: ID 0000:0000  
**Bus 002 Device 002: ID 064e:a101 Suyin Corp.** 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```
(The bold is my web cam).

---

### Post by koolguynet on 2008-08-14
> **sergiom99 said:**
> post the output of this command:
lsusb

You'll find there the hard-specs of your cam to search the forums for specific solutions.

Also, which program are you trying your cam with? cheese? IM apps?

Here is my output from lsusb:

> Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0471:0815 Philips 
Bus 001 Device 005: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 003: ID 05ca:1810 Ricoh Co., Ltd 
Bus 001 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 001: ID 0000:0000 

I am trying to get it working for IM programs but cheese won't work either.  I have tried some of the instructions for this camera, but to no avail.  I am wondering if it has to do with my OS being 64 bit?

---

### Post by sergiom99 on 2008-08-15
this same issue was brought up a few days ago:
[http://ubuntuforums.org/showthread.php?t=883349&highlight=05ca%3A1810+Ricoh](http://ubuntuforums.org/showthread.php?t=883349&highlight=05ca%3A1810+Ricoh)
check the links at the bottom of the thread.
maybe it does has something to with 64bit. Maybe you could try booting with a 32-livecd.

---

### Post by koolguynet on 2008-08-17
I finally got it to work.  I compiled it using these instructions:
[http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation)

---

### Post by mshanmuga on 2009-12-30
I have HP Pavillion dv9000 and have 9.10 64bit installed. 
 lsusb output doesnt show any web cam  devices.
Can somebody tell me how to get the internal web cam working
Thx

---

