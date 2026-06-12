---
title: "Wisecom Modem Installation (USB)"
date: 2010-08-21
forum: Hardware
---

### Post by and003 on 2010-08-21
I am interested in installing an external modem so I can send faxes from my home. The modem I have is a Wisecom Accelerator Pro 56K External Voice/Fax Modem with an RS-232 serial port. This modem is connected to my computer by a special cable that is plugged into one of my computer's USB ports. The usbserial driver appears to have been activated, as is shown here:

and003@TigerUbuntu3300C:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 03f0:7711 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

To clarify, my Wisecom modem is connected at Bus 003, designated as Device 003, and is identified as a Prolific Technology PL2303 serial port. I plan to use the eFax software package. My modem's address is /dev/ttyUSB0. It should be noted that I don't intend to use my modem for surfing the Internet as I use DSL for net surfing and will continue to do so.

Simply put, I wish to learn if I need to do anything special to make my Wisecom modem work in Ubuntu while connected to a USB port.

---

### Post by and003 on 2011-12-08
I have decided to purchase a U.S. Robotics modem that is Linux ready. Therefore, I am marking this thread as 'solved.'

---

