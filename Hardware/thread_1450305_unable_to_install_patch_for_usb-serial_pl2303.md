---
title: "unable to install patch for usb-serial pl2303"
date: 2010-04-08
forum: Hardware
---

### Post by madaptive on 2010-04-08
I am using a usb-serial port to talk to a motor and have been unable to do so.

my lsusb output is:

us 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 413c:2106 Dell Computer Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

then following some Ubuntu form threads I mapped the usb to tty using the following command:

sudo modprobe usbserial vendor=0x067b product=0x2303

dmesg showed that the usb was mapped to ttyUSB0 however I could still not talk to the motoer. I am using the following command:

echo "/command" > /dev/ttyUSB0

searching on web I found the following link for a patch: [http://koti.mbnet.fi/lonnberg/pl2303x.html](http://koti.mbnet.fi/lonnberg/pl2303x.html)

I have followed the instruction to install the patch but I get the following error message:

root@supernova2:/usr/src/linux-headers-2.6.32.6/drivers/usb/serial# patch -u /usr/src/linux-headers-2.6.32.6/drivers/usb/serial/pl2303.c /usr/src/linux-headers-2.6.32.6/drivers/usb/serial/pl2303x.patch
patching file /usr/src/linux-headers-2.6.32.6/drivers/usb/serial/pl2303.c
Hunk #1 FAILED at 176.
Hunk #2 FAILED at 394.
Hunk #3 FAILED at 421.
Hunk #4 FAILED at 468.
4 out of 4 hunks FAILED -- saving rejects to file /usr/src/linux-headers-2.6.32.6/drivers/usb/serial/pl2303.c.rej

Could someone please help me with this problem? Thank you very much.

---

### Post by Tii on 2010-07-13
hello,

I have the exact same problem as I'm trying to use a printer thru this USB to serial port /dev/ttyUSB0

dmesg gives this :

[  532.732170] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  532.892547] usb 2-1: configuration #1 chosen from 1 choice
[  532.894560] pl2303 2-1:1.0: pl2303 converter detected
[  532.908568] usb 2-1: pl2303 converter now attached to ttyUSB0

but nothing happens when I try to echo  on it !

I really need help please

---

### Post by Tii on 2010-07-15
Yesterday, I was able to write on the printer (connected to my USB-to-serial P2303) with the 

echo "hello world" > /dev/ttyUSB0 

by previously changing port configuration with minicom 

I set the transfert rate to 9600 and switch the parity check to OFF.

It's a step forward but no solution as I don't know how to make it permanent and it only print from terminal (not from application !)

anyone ?? please help !

thx

---

### Post by Tii on 2010-07-29
Hello again,

I found out a solution you might try :

```
stty -F /dev/ttyUSB0 9600
```

as I realised that the problem was linked to the speed of the tty

if you can echo things on it after this, you might just add this line to your .bashrc  :)

hope this helped ...

---

