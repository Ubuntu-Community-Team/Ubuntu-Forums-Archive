---
title: "USB to Serial, no keyboard input"
date: 2009-05-22
forum: Hardware
---

### Post by stevy99 on 2009-05-22
Hello, currently I'm trying to get a serial connection working from my laptop to my server. As the laptop does not have a serial port I've bought a USB to serial converter. The odd thing is that I've managed to make it work (i.e. I can see the BIOS output and the login prompt over the connection), but keyboard input doesn't do anything. Maybe I've forgotten something.. Does someone know?

Some more info: 
lsusb shows: 002 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
lsmod shows that pl2303 and usbserial are loaded.

Also, when connecting the NULL modem cable (without the USB converter) directly between the server and another PC I can log in to the server and manage it. 

Laptop is running Ubuntu 9.04 64-bit. Server Ubuntu-server 9.04 32-bit. (test pc was running Knoppix 5.1.1, also tested with Systemrescuecd 1.1.5).

So there seems to be a problem with either the driver, the config or the cable it self and it's not debian specific since the systemrescuecd is based on Gentoo).

---

### Post by stevy99 on 2009-05-22
Right now I've booted to Windows Vista. Same problem. I can see the BIOS output and get the login prompt in Putty, but I can't type anything into the screen, so logging in is not possible.

This means that it has to be either the USB-to-serial converter or the server configuration. 
Here's my /etc/event.d/ttyS0 (server side):
```

# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 115200 ttyS0

```I copied it from:
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

---

