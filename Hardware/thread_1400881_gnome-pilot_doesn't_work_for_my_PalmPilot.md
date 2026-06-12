---
title: "gnome-pilot doesn't work for my PalmPilot"
date: 2010-02-07
forum: Hardware
---

### Post by ultem_ulfing on 2010-02-07
*(Please excuse this question is already posted at LinuxQuestions.org. Due to its very specific nature I want to present it to you competent people here as well!*)

I have found an original PalmPilot in very good condition and bought it for 10 bucks. Now I want to synchronize it with my Ubuntu system using gnome-pilot. It once connected successfully when I reset the Palm, but when I tried to install an .prc, using 'gpilot-install-file', the 'gpilotd' crashed. After restarting it, it wouldn't work again and gnome-pilot seems to constantly crash.

Can you please help? -.-

Additional information:
- PalmOS is 3.3, has the 'Palm-III memory upgrade'
- the dock's DE-9 RS232 cable is connected to my 'ThinkPad Advanced Mini Dock', this 
additional interface is activated in my BIOS
- the connection speed matches (57600 bits/s)
- first it was recognized on ttyS0, after changing serial-settings in BIOS it appeared on ttyS1. Both don't work atm.
- Ubuntu just updated to 2.6.31-19-generic ; gnome-pilot is 2.0.17-0ubuntu2

> 
Device Settings
Name: Cradle
Type: Serial
Timeout: 2
Device: /dev/ttyS1
Speed: 57600

PDA Settings
Owner: Ultem Ulfing
PDA ID: 5
Name of PDA: MyPDA
Local folder: /home/ultem/MyPDA
Charset of PDA: CP1252> 
ultem@ultem-laptop:~$ sudo ls -la /dev/ttyS* 
crw-rw---- 1 root dialout 4, 64 2010-02-07 11:01 /dev/ttyS0 
crw-rw---- 1 root dialout 4, 65 2010-02-07 11:01 /dev/ttyS1 
crw-rw---- 1 root dialout 4, 66 2010-02-07 11:01 /dev/ttyS2 
crw-rw---- 1 root dialout 4, 67 2010-02-07 11:01 /dev/ttyS3 > T61 BIOS 2.24 (7LETC4WW)
...
Serial port: Enabled
Base I/O adress: 3F8
Interrupt: IRQ 3
...
Legacy Devices on Mini-Dock: Enabled

---

### Post by NUboon2Age on 2010-06-22
Did you get it working?  If so please give details.  Thanks!

---

