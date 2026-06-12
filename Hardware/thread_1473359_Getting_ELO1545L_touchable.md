---
title: "Getting ELO1545L touchable"
date: 2010-05-05
forum: Hardware
---

### Post by FSiever on 2010-05-05
Hello,

i purchased an ELO 1545L Touchmonitor to use with Ubuntu 10.04.
As my Laptop doesn´t have any serial port, i connected an usb to serial cable.
This cable is shown when i type "lsusb"
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 6547:0232 Arkmicro Technologies Inc. ARK3116 Serial <-- this is the cable
Bus 003 Device 003: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a116 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```But here is no ELO Touch listed.
I tried to change xorg.conf, with result, that X didn´t start anymore.

I installed evtouch with no success and elotouch hasn´t success too.

i tried all these Links, but no success :

[http://ubuntuforums.org/archive/index.php/t-579155.html](http://ubuntuforums.org/archive/index.php/t-579155.html)

[http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html]("http://stz-softwaretechnik.com/%7Eke/touchscreen/evtouch.html")

[http://knx-user-forum.de/knx-eib-forum/6951-visu-elo-touch-1515l.html](http://knx-user-forum.de/knx-eib-forum/6951-visu-elo-touch-1515l.html)

I can see the Desktop on the ELO but i can´t get any touch.

when i use

```
cat < /dev/ttyUSB0
```an i touched the ELO, i get many output on the console.

Do you have an idea, how to get my touchscreen touchable ?

Florian

---

### Post by 19jam81 on 2010-05-20
Hi,

i got exactly the same Problem. Same Tochscreen, same USB-to-Serial-Cable, same Operating System.

I also tried with a Serial Cable and i tried with Hardy. The same Problem everywhere.

Is there anyone out there who can help?

thanks,

Tobias

---

