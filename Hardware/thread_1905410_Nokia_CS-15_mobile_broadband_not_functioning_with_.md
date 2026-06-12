---
title: "Nokia CS-15 mobile broadband not functioning with lubuntu 11.10"
date: 2012-01-06
forum: Hardware
---

### Post by Dakkus on 2012-01-06
My Nokia CS-15 internet stick isn't recognized at all by Network Manager on my fresh Lubuntu 11.10 installation.

Installing usb_modeswitch brought me so far that the led on the device starts blinking red if I have it attached while starting the computer.
The possibility to connect to mobile broadband however still doesn't appear on the menu I get by clicking on the network manager system tray icon. The menu shows precisely the same things (that is, a pile of my neighbours' boringly password-protected wireless networks), no matter whether the CS-15 is attached to the computer or not.

This is what lsusb outputs (among other stuff) if I have had the stick attached already when I boot the computer:
**Bus 001 Device 005: ID 0421:0612 Nokia Mobile Phones **

If I attach the device while lubuntu is already running, lsusb returns this:
**Bus 001 Device 006: ID 0421:0610 Nokia Mobile Phones CS-15 (Internet Stick 3G modem)**

When trying to do [b]usb_modeswitch -v 0x0421 -p 0x0610 -m 0x01 -M "5553424312345678000000000000061b000000020000000000000000000000"
[/b], I get this:

[b]Looking for default devices ...
 Found devices in default mode, class or configuration (1)
Accessing device 006 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached [/b]

after which nothing happens.

Some other things I have edited and might be relevant:

[b]dakkus@donkerwit-jr:~$ cat /etc/wvdial.conf 
[Dialer Defaults]
Modem = /dev/ttyACM1
Init = AT+CGDCONT=1,"IP","internet"
Phone = *99#
Stupid Mode = 1
Username = " "
Password = " "


dakkus@donkerwit-jr:~$ sudo wvdialconf 
[sudo] password for dakkus: 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- CS-15 R2.6.2-0634487
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyACM1<*1>: ATQ0 V1 E1 -- OK
ttyACM1<*1>: ATQ0 V1 E1 Z -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM1<*1>: Modem Identifier: ATI -- CS-15 R2.6.2-0634487
ttyACM1<*1>: Speed 4800: AT -- OK
ttyACM1<*1>: Speed 9600: AT -- OK
ttyACM1<*1>: Speed 19200: AT -- OK
ttyACM1<*1>: Speed 38400: AT -- OK
ttyACM1<*1>: Speed 57600: AT -- OK
ttyACM1<*1>: Speed 115200: AT -- OK
ttyACM1<*1>: Speed 230400: AT -- OK
ttyACM1<*1>: Speed 460800: AT -- OK
ttyACM1<*1>: Max speed is 460800; that should be safe.
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 -- [/b]

wvdial stops doing anything after showing the two dashes (--).

dakkus@donkerwit-jr:~$ cat /etc/udev/25-mokkulat.rules 
BUS=="usb", SUBSYSTEM=="block", SYSFS{idVendor}=="0421", SYSFS{idProduct}=="0610", ACTION=="add", RUN+="/usr/bin/eject -s %N", OPTIONS+="last_rule"

dakkus@donkerwit-jr:~$ sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
ERROR
--> Invalid dial command.
--> Disconnecting at Sat Jan  7 02:21:34 2012
dakkus@donkerwit-jr:~$ 
[/b]

This also happens if I change ttyACM1 to ttyACM0 in /etc/wvdial.conf.

And as the last and, well, probably the least, after all:
[b]dakkus@donkerwit-jr:~$ uname -a
Linux donkerwit-jr 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux[/b]

So, what am I missing? The device functioned well when I was still using the 9.04 based eeebuntu on this computer. It also funtioned on another computer with standard ubuntu 11.10 installed on it and currently works on another computer that should be identical to this one, only running a very outdated eeebuntu.
Any ideas of how I could get the CS-15 to function on this lubuntu installation? I kinda like the speed of lubuntu very much and would definitely want to use it seriously. Both of my computers are Asus eee pc 4G.

---

