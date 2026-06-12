---
title: "No port for Cura"
date: 2016-04-24
forum: Hardware
---

### Post by GettingNowhere on 2016-04-24
Hi all.
Well, I took the plunge and clean installed 16.04 64 bit.
Seems to be going well, except for my now useless 3D printer (Makerbot)
I installed Cura 15.04.5 as well as 
pypy
python-gpgme
python-opengl
python-numpy
python-serial
python-setuptools
curl
and arduino
as suggested by some website or other

There is no way Cura will see the USB port ttyACM0
It can't find the baud rate if on Auto, and just (eventually) says "Closed" if I force ttyACM0 at 115200.
There are quite a lot of people with this problem on the Cura forums, but very little in the way of answers

The computer can see the printer:

```
 dmesg | tail -n15
[ 1257.755999] usb 5-1: new full-speed USB device number 4 using ohci-pci
[ 1257.933224] usb 5-1: New USB device found, idVendor=23c1, idProduct=d314
[ 1257.933238] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=220
[ 1257.933246] usb 5-1: Product: The Replicator
[ 1257.933252] usb 5-1: Manufacturer: MakerBot Industries
[ 1257.933257] usb 5-1: SerialNumber: 5543733343735130C082
[ 1257.935430] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
[ 2398.824233] usb 5-1: USB disconnect, device number 4
[ 2402.210473] usb 5-1: new full-speed USB device number 5 using ohci-pci
[ 2402.383729] usb 5-1: New USB device found, idVendor=23c1, idProduct=d314
[ 2402.383741] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=220
[ 2402.383749] usb 5-1: Product: The Replicator
[ 2402.383755] usb 5-1: Manufacturer: MakerBot Industries
[ 2402.383760] usb 5-1: SerialNumber: 5543733343735130C082
[ 2402.386240] cdc_acm 5-1:1.0: ttyACM0: USB ACM device

```

I've done:
sudo usermod -a -G tty $USER
sudo usermod -a -G dialout $USER
cd /dev/serial/by-id
sudo chown <me> usb*
sudo chgrp <me> usb*
sudo gpasswd -a <me> dialout
rebooted
but nothing worked.
Anybody any ideas?

---

### Post by GettingNowhere on 2016-04-26
I've now also installed cura-engine

Still doesn't work.....

---

### Post by GettingNowhere on 2016-05-04
Anybody?

---

### Post by GettingNowhere on 2016-05-09
If I put my ear up against the monitor, I can hear the sea.......

---

### Post by GettingNowhere on 2016-05-26
Tide must be out.

---

### Post by GettingNowhere on 2016-05-28
I guess it's a no then.

---

