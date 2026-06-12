---
title: "U Blox 7 GPS - Glonass Help.."
date: 2015-10-25
forum: Hardware
---

### Post by el_bizarro on 2015-10-25
I'm trying to get a Ubox 7 USB GPS/Glonass Adapter to work with Lubuntu..

My Ideal solution is to Put it into my Vehicle with a Raspberry PI but I realize this isn't the forum for that..

However..

In Lubuntu and also Raspbien I have Plugged in the USB Adapter and indeed it is Detected..

The Issue I am having is when I check its Configuration it is set as a /dev/ttyACM0 and not /dev/ttyUSB0..

All of the Programs that I have Tried are looking for a USB Adapter and I do not see any way to Get this Device to Work in any Navigation Programs..

xgps and cgps wont work..

Obviously in Windows it's picked up as a USB and Ultimately given a Serial Port but in Linux this seems to be the Issue..

sudo gpsd -N -n -D 2 /dev/ttyACM0 does not seem to solve the Issue However..

lsusb - Bus 002 Device 003: ID 1546:01a7 U-Blox AG 

dmesg | grep tty 

[    0.000000] console [tty0] enabled
[    1.600743] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    9.715269] systemd[1]: Created slice system-getty.slice.
[13810.760882] cdc_acm 2-1:1.0: ttyACM0: USB ACM device

This machine has a serial Port so I'm guessing the 1st 2 lines are for that..

sudo cat /dev/ttyACM0 returns data in Terminal..

My Question I guess is how do I make this Device work in Either a Serial or USB mode so that GPS Software will communicate with it ?..

Thanks

Robert..

---

