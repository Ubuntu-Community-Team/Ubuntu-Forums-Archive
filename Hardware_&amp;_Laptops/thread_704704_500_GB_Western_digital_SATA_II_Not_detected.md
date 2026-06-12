---
title: "500 GB Western digital SATA II Not detected"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by starfox5194 on 2008-02-22
I have tried using the command line installation of ubuntu gusty gibbon and when it gets to hdd detection it doesn't work.

things i've tried

Setting my sata hdd as ide in bios
googling it


other problems

i don't have a floppy drive

---

### Post by jmate24 on 2008-02-25
First turn off your computer.
Second you have to have the jumpers on the hard drive set to sata II only.
Third Make sure that your bios sata controller is enabled and set to ide. there might be a jumper if it is a pci card or on the motherboard.
Fourth get a copy of Ubuntu 7.10 Live CD and turn on the computer then insert it in to the CD/DVD drive and reboot.
Once it is in the Live CD environment Open Up a terminal and type sudo fdisk -lu.
if you see the drive in the output then close the window and click the install icon on the desktop.
Finaly answer all of the questions and complete the steps, then you should have a usable computer in 25-45 minutes.

---

