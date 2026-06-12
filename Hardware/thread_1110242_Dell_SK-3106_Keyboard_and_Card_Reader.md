---
title: "Dell SK-3106 Keyboard and Card Reader"
date: 2009-03-29
forum: Hardware
---

### Post by lingenfr on 2009-03-29
Using the instructions [here]("https://help.ubuntu.com/community/CommonAccessCard"), I have an SCR reader working, but I picked up a Dell combo keyboard/cardreader and was hoping to get it working. It seems to be recognized, but when I run pcsc_scan it says card removed even though the card is inserted. Also, the light on the keyboard for the card reader is not lit regardless of whether a card is inserted or not. When I plug it in I get:

[11080.536015] usb 7-2: new full speed USB device using uhci_hcd and address 8
[11080.722174] usb 7-2: configuration #1 chosen from 1 choice
[11080.728382] input: Gemplus Dell USB Smartcard Keyboard as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input2
[11080.772613] input,hidraw1: USB HID v1.00 Keyboard [Gemplus Dell USB Smartcard Keyboard] on usb-0000:00:1d.2-2

lsusb says:

Bus 008 Device 002: ID 07cc:0301 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 008: ID 413c:2100 Dell Computer Corp. SK-3106 Keyboard
Bus 007 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and pcsc_scan says:

PC/SC device scanner
V 1.4.14 (c) 2001-2008, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.99
Scanning present readers
0: Dell keyboard SK-3106 00 00

Sat Mar  7 11:51:42 2009
 Reader 0: Dell keyboard SK-3106 00 00
  Card state: Card removed, 

When the card is inserted. Has anyone gotten this working? I moved this from the 64-bit forum as I switched to 32-bit and still have the same problem.

---

### Post by lingenfr on 2009-04-11
Bump.

---

### Post by ixpl on 2009-06-05
Hey if have had any luck with this shoot me a message. I have picked up a used one of these and would like to implement it in my system.

---

### Post by lingenfr on 2009-07-07
Bump.

---

