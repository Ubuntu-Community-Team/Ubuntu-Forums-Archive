---
title: "Xerox Phaser 6115MFP"
date: 2012-08-09
forum: Hardware
---

### Post by RRMcMillan on 2012-08-09
I have a Xerox Phaser 6115MFP connected to my HP Pavilion a1737 with an AMD A64x2 processor and 4GB RAM. I am running Precise Pangolin 64bit and VB with Win7 and WinXP both functional

I ran lsusb and it shows the following:

roy@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 03f0:0b0c Hewlett-Packard Wireless Keyboard and Optical Mouse receiver
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 001 Device 005: ID 0924:3d5b Xerox Phaser 6115MFP TWAIN Scanner
roy@ubuntu:~$ 

My question is three fold:

1.) If the USB ports and system recognise it for what it is, why won't Xsane or Simple Scan recognise it?

2.) Is this a software issue that I just need an application that will recognise it or do I need a driver?

3.) If it is a driver issue, why can't I find it on the web?

Thanks in advance for your help!!

---

### Post by gordintoronto on 2012-08-09
Ubuntu can identify the device, but it can't invent a driver. You could ask Xerox why there is no Linux driver.

---

