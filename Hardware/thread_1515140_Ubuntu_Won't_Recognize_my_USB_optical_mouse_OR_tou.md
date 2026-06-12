---
title: "Ubuntu Won't Recognize my USB optical mouse OR touch pad?"
date: 2010-06-21
forum: Hardware
---

### Post by DillyT33 on 2010-06-21
I am using the toshiba satellite a505.

I am actually looking to replace Windows 7 with Ubuntu as my OS.

I made up the live CD and ran the demo. But noticed that my touch pad wasn't working.

I was not surprised the USB optical mouse(Which is a Dynex - Mod #: DX-WOM2) wasn't working because when i tried fedora 13 the other day it didn't work either.

But the Touch Pad doesn't even work so i have no cursor control when i run Ubuntu. 

I played around with the demo using the keyboard. Haha.

I actually became pretty knowledgeable about the shortcuts in Ubuntu.

But theres no way i can replace Windows 7 with Ubuntu if it wont recognize my hardware.

So any help, tips, advice, & comments are appreciated!

I will post my system specs. below just in case there needed. 




    Machine name: DILLION-PC
   Operating System: Windows 7 Home Premium 64-bit (6.1, Build 7600) (7600.win7_rtm.090713-1255)
           Language: English (Regional Setting: English)
System Manufacturer: TOSHIBA
       System Model: Satellite A505
               BIOS: InsydeH2O Version 1.20
          Processor: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz (4 CPUs), ~2.1GHz
             Memory: 4096MB RAM
Available OS Memory: 3894MB RAM
          Page File: 1731MB used, 6056MB available
   


-----------
USB Devices
-----------
+ USB Root Hub
| Vendor/Product ID: 0x8086, 0x3B3C
| Matching Device ID: usb\root_hub20
| Service: usbhub
| 
+-+ Generic USB Hub
| | Vendor/Product ID: 0x8087, 0x0020
| | Location: Port_#0001.Hub_#0001
| | Matching Device ID: usb\class_09
| | Service: usbhub



------------
PS/2 Devices
------------
+ Standard PS/2 Keyboard
| Matching Device ID: *pnp0303
| Service: i8042prt
| 
+ Terminal Server Keyboard Driver
| Matching Device ID: root\rdp_kbd
| Upper Filters: kbdclass
| Service: TermDD
| 
+ Synaptics PS/2 Port TouchPad
| Matching Device ID: *syn191a
| Upper Filters: SynTP
| Service: i8042prt
| 
+ HID-compliant mouse
| Vendor/Product ID: 0x1241, 0x1166
| Matching Device ID: hid_device_system_mouse
| Service: mouhid
| 
+ Terminal Server Mouse Driver
| Matching Device ID: root\rdp_mou
| Upper Filters: mouclass
| Service: TermDD



If any other specs. are needed let me know.

---

### Post by DillyT33 on 2010-06-21
Hey guys, any chance this is because my system is 64-bit and i have the 32-bit installation on the CD?

---

### Post by DillyT33 on 2010-06-22
Anyone have any idea??!!

---

### Post by HDTimeshifter on 2010-07-10
I can't get my GE PS/2 optical mouse to work with my desktop system either.  Below is my configuration.  I'm going to try plugging it into my Windows XP system to see if it is Ubuntu or the mouse itself.  The laser does light up.

Ubuntu 10.0.4 LTS 64-bit
ASUS P5Q Pro motherboard

GE WK3803 PS/2 optical mouse won't work.  No cursor movement when I boot up with this mouse plugged in.  Anybody with this mouse able to get it to work?

---

### Post by AltomineUK on 2010-07-10
32-bit software will nearly always work with 64-bit hardware, unless it's extraordinarily old. So no...that's not the case.

Type this to check if your inputs appear on Ubuntu at all.

```
xinput list
```

---

### Post by lidex on 2010-07-10
You are not alone
Have a look here:
[http://www.linlap.com/wiki/toshiba+satellite+a505]("http://www.linlap.com/wiki/toshiba+satellite+a505")
More (much more):
[http://www.google.com/search?q=Toshiba+Satellite+A505&sitesearch=ubuntuforums.org]("http://www.google.com/search?q=Toshiba+Satellite+A505&sitesearch=ubuntuforums.org")

---

