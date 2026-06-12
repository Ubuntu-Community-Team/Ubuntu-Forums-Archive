---
title: "Epson Stylus Photo RX 420 Multifunction"
date: 2006-08-26
forum: Hardware &amp; Laptops
---

### Post by Dr_Freemanstein on 2006-08-26
Hi guys,

Trying to get my multifunction to work with Ubuntu 6.06 LTS.
I have done the add printer bit, which it found fine, but I am having real problems getting it to detect the scanner.

Anyone else had this (or similar) problem??

_System:_

< Processor >       AMD Athlon(tm) XP 2400+
< Mainboard >       Gigabyte Technology Co., Ltd. GA-7VA-A
< Memory >          768MB DDR-SDRAM
< Hard Disks>       
1:  Maxtor 6Y080L0 (76GB) [Partitioned into 66GB (NTFS), 500MB (Swap), 10GB (ext3)
2:  ST340810A (37GB) [One partition of 37GB (FAT32)]
< Optical Drives >  
1: ATAPI CDRW 52X32 (CD 52X Rd, 52X Wri)
2: PIONEER DVD-RW  DVR-110D (CD 40X Rd, 40X Wr) (DVD 5X Rd, 5X Wr)
< Video Adapter >   NVIDIA GeForce FX 5200
< Sound Card >      Creative SB Live! series
< Input Devices >   
Keyboard: Standard 101/102-Key or Microsoft Natural PS/2 Keyboard 
Mouse:    PS/2 Compatible Mouse 
< Printer >         EPSON Stylus Photo RX420 Series
< Operating System(s) > 
Windows System:   Microsoft Windows XP/2002 Home 5.01.2600 (Service Pack 2)    
Linux System:     Ubuntu 6.06 LTS (Dapper Drake)

---

### Post by DoctorMO on 2006-08-27
Does it work with windows?

Have you tried looking at SANE website to see if the scanner is supported there? [http://www.sane-project.org/](http://www.sane-project.org/)

It says the RX-425 is supported perhaps RX-420 will use the same driver. could you do an lsusb and post the results? I can always add your scanner to the epson sane back end if it works and this will lead to detection.

---

### Post by DoctorMO on 2006-08-27
A little bit of digging shows that sane has suported the RX420 for quite a while.

You should be able to see it if you run `sane-find-scanner`

---

### Post by Dr_Freemanstein on 2006-09-01
Thanks for the help DoctorMo  :D

---

