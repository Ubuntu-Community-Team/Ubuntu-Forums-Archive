---
title: "Kodak EasyShare C195 doesn't mount"
date: 2011-05-09
forum: Hardware
---

### Post by kbogle on 2011-05-09
I have a Kodak Easy Share C195 Digital Camera.  It will not mount or even be recognized by Ubuntu Natty.  

lsusb output when Camera is connected:


kbogle@kbogle-ThinkPad-T61:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 040a:0600 Kodak Co. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Can someone please help.....

---

### Post by dli8ilb on 2011-05-12
same issue here (10.10).

lsusb:  Bus 006 Device 003: ID 040a:060c Kodak Co.

edit: after introducing the camera on my windows partition, i was able to at least save the pictures off it from there (was hoping i wouldn't have to do that... odd thing is, now the lsusb ID has changed:

lsusb:  Bus 006 Device 003: ID 040a:060**0** Kodak Co.

and the camera says:

"For operation with printers, picture frames and non-computer devices.  Please refer to the Extended Users Guide at www.kodak.com/go/support."

so, it thinks ubuntu is a non-computer device?  oh well kbogle, guess we'll have to suck it up and get card readers to pull our images for now ](*,)

---

### Post by rramsay on 2011-06-04
Same issue, I'm running 11.04 I hope someone with more smarts than me fixes this.:(:(

---

### Post by Areia on 2011-06-10
Same problem here! Tried with Gtkam... and nothing. Please help us!!!

---

### Post by fand0r on 2011-07-19
> **Areia said:**
> Same problem here! Tried with Gtkam... and nothing. Please help us!!!

On Camera enter setup and in Software section on the bottom choose Other Software instead of Kodak Downloader.

CHEERS!:P

---

### Post by stanoly on 2012-05-30
I discovered in these cameras when you push the red button "share", then the wrench which opens settings then scroll down to computer connection. There is an option "other application" or kodak software. Choose "other application" Then connect camera to the computer. Your camera will then be recognized on Ubuntu. I have an easyshare m532.
Hope this helps somebody.

---

