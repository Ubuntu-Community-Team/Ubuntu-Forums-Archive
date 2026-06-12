---
title: "Usb midi keyboard plug&amp;play."
date: 2012-05-08
forum: Hardware
---

### Post by LucaFiore on 2012-05-08
Hi to all, 
i have a Novation Impulse 61, and a M-audio 88Es.

when I connect them, they are recognized by the system, but in the jack connect, or in the reaper midi options, I don't see their.

this is my lsusb and my aconnect -i & aconnect -o:

------------------------------------------------
(~) % lsusb 
Bus 007 Device 004: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 07ca:a309 AVerMedia Technologies, Inc. HP DVB-T TV Tuner [HP dv6-1190en]
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 1235:001b Novation EMS <------------------------------------------------------------------------------- this is my keyboard.
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
------------------------------------------------
~) % aconnect -i 
client 0: 'System' [type=kernel]
0 'Timer '
1 'Announce '
client 14: 'Midi Through' [type=kernel]
0 'Midi Through Port-0'
------------------------------------------------
(~) % aconnect -o 
client 14: 'Midi Through' [type=kernel]
0 'Midi Through Port-0'
------------------------------------------------

any suggestion??? 

Thanks in advice.

---

