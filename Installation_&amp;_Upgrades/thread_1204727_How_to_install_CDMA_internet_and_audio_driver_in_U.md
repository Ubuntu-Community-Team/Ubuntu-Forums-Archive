---
title: "How to install CDMA internet and audio driver in UBUNTU 9.04"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by soumen.mondal on 2009-07-05
I have Compaq C700 presario laptop. Any one please tell me how to connect CDMA USB internet and how to install audio driver?

---

### Post by zwdev on 2009-07-05
I use wvdial to connect on my usb cdma modem here is how:

1. In terminal type : sudo wvdialconf
2. sudo gedit /etc/wvdial.conf 
 Edit the file to look something like this


[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = USB Modem
Phone = #777
Username = dtac
Password = dtac
stupid mode = 1 


3: sudo wvdial

4: without closing the terminal open your browser and browse away.

That should do it. Its working for me;

---

