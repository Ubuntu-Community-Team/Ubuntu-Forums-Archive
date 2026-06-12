---
title: "Novatel 727"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by Jermski on 2007-10-19
Has anyone had any luck with the Novatel 727?

---

### Post by yottabit on 2008-03-19
> **Jermski said:**
> Has anyone had any luck with the Novatel 727?

I keep trying to get the usbserial driver to initialize but no luck... using:
```
$ sudo modprobe -rv usbserial; sudo modprobe -v usbserial vendor=0x1410 product=0x4100rmmod /lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/usbserial.ko
insmod /lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/usbserial.ko vendor=0x1410 product=0x4100 vendor=0×1410 product=0×4100
```

The double vendor & product IDs are because I also created an option file, /etc/modprobe.d/usbserial, so that I don't have to specify the product & vendor each time:
```
options usbserial vendor=0×1410 product=0×4100
```

But alas still no luck, dmesg:
```
$ dmesg
...
[ 3672.600000] usbcore: deregistering interface driver usbserial_generic
[ 3672.600000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial deregistering driver generic
[ 3672.600000] usbcore: deregistering interface driver usbserial
[ 3672.640000] usbcore: registered new interface driver usbserial
[ 3672.640000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 3672.640000] usbcore: registered new interface driver usbserial_generic
[ 3672.640000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
$  ls /dev/ttyU* /dev/ttyA*
ls: /dev/ttyU*: No such file or directory
ls: /dev/ttyA*: No such file or directory
```

And to make sure product & model are correct, lsusb:
```
$ lsusb
...
Bus 001 Device 005: ID 1410:4100  
...
```

Any hints??? My old V620 Cardbus EVDO card worked just fine in Linux...

---

### Post by chilinski on 2008-03-19
It works fine for me. I put the usbserial in the blacklist at /etc/modprobe.d/blacklist so it wouldn't load at boot time. 

Then, when I want to use the device, I plug it in and wait for it to appear on the desktop. Then I umount/eject it. Then I run a small script:

#!/bin/sh
sudo modprobe usbserial vendor=0x1410 product=0x4100
sleep 2
sudo wvdial

And it works just fine. There are detailed instructions on the sprint.com website for installing the device (which you must have seen to have gotten the vendor and product ID). I followed those, preferring to use wvdial over KPP because wvdial was already installed, and I didn't want KDE stuff.

---

### Post by chilinski on 2008-03-19
By the way, wvdial.conf looks like this:

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = USB Modem
Phone = #777
Username = ''
Password = ''
Carrier Check = no
Stupid Mode = yes

---

### Post by yottabit on 2008-03-19
thanks for the details... I am using the VZW version, not Sprint PCS, but it should work the same...

My problem is that when I load the usbserial module, exactly in the way you have specified, I never get the ttyUSB? or ttyACM? nodes populated in /dev. :( And if I create the nodes myself (yes, with the correct major/minor) it still doesn't work.

Can you point me to the specific Sprint docs you mentioned?

J

---

### Post by Jermski on 2008-04-20
Here's a link directly to the Sprint PDF for setting up all the Sprint Connection Cards with Linux.

[http://www.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

---

### Post by yottabit on 2008-04-20
I found that the latest kernel worked fine with my usb727... but not the stock 7.10 kernel. Looking forward to the release of 8.04! Only 4 more days!

---

### Post by tdubois65 on 2008-05-28
OK - I HAD this thing working last week.  It seems to be a different procedure by the day.  I'm on 8.04, using KPPP for connection.

First issue:  It seems to take a few minutes for my PC to recognize the modem.  Any ideas?

Second issue:  Thunderbird 'sees' the network connection, but Firefox does not.  Pidgin saw it yesterday, but today does not...  any ideas?

Third issue:  The instructions from Sprint are obviously from an older version of Ubuntu.  The whole network config thing does not work for me.  My networking icon shows disabled and nothing I do seems to get it to recognize the PPP connection.  

I'm on the verge of throwing in the towel and taking the card back and/or going back to Windows.  I need this to be reliable as my livelihood depends on it.

---

### Post by yottabit on 2008-05-28
I haven't had time to play with 8.04 yet... I might be able to later this week and let you know what I find.

I did use Windows to configure my USB727 into NDIS mode (presents itself to Windows as a network card so it's "always-on"--it dials and maintains the connection by itself, without use of the VZ Access software), but Ubuntu 8.04 didn't show anything special after configuring in this way... I recall the kernel didn't even notice any kind of network interface at all, so I'm thinking for some reason this NDIS mode depends on the Windows driver, and not as much on the USB727 device itself as I had hoped.

Anyway, I'll see what I get on this end later this week when I get a chance to use it in 8.04.

---

