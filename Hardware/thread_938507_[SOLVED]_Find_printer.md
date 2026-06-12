---
title: "[SOLVED] Find printer"
date: 2008-10-05
forum: Hardware
---

### Post by mpierce on 2008-10-05
Using KUbuntu 8.04.1 on a newly built box (fresh install). 

Box has no old parallel port lp0 connection so I got a cable and connected my HP 2550L Color LaserJet via usb. Printer works on XP box fine so, it will print if I can configure it. 

Copied old cups.conf & printer.conf to new box. Test page not printing as it can't find printer. 

lsusb shows: Bus 001 Device 003: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port

dmesg shows:
[   43.384696] usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x067B pid 0x2305

Haven't fooled with changing anything at: [http://localhost:631/printers/LaserJet2550l](http://localhost:631/printers/LaserJet2550l) 

Have tried to locate it using the HP Device Manager by manually finding the device. It asks for the USB ID of the printer and will only accept
000:000, so I'm lost as it is not showing that format.

---

### Post by mpierce on 2008-10-05
OK - let's close the thread. I had to use Cups Admin and change the location. I then copied the printer link and pasted it into my XP machine, configured printer through KDE on my other linux box and voila - printing fine.

---

