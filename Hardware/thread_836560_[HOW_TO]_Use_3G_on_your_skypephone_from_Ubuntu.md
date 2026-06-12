---
title: "[HOW TO] Use 3G on your skypephone from Ubuntu"
date: 2008-06-21
forum: Hardware
---

### Post by apoth on 2008-06-21
Connect the phone to your computer via the USB lead.

Edit /etc/wvdial.conf to read:

```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 115200
Init = ATH
Init2 = ATE1
Init3 = AT+CGDCONT=1,"IP","three.co.uk","",0,0
Dial Command = ATD
Phone = *99#
Username = a
Password = a
Stupid Mode = yes
Carrier Check = no

```

Turn off any network interfaces you have up and running:

```
sudo ifconfig eth0 down
sudo ifconfig eth1 down
...
```

Load the kernel driver:

```
sudo modprobe usbserial vendor=0x1614 product=0x0804
```

Run wvdial:

```
sudo wvdial
```

Add the default route:

```
sudo route add default gw 10.64.64.64
```

Hopefully you're now able to browse to google.

If not, the following commands should help you diagnose any problems:

```
ifconfig
route -n
lsusb
```

---

### Post by Nazareth on 2008-10-14
Hello, 
I'm considering getting the Skypephone S2, and was wondering if these instructions work out of the box, or whether you require a separate data contract with Three in addition to the normal voice (and free skype) contract.

---

