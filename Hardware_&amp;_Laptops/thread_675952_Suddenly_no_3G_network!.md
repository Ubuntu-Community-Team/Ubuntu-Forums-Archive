---
title: "Suddenly no 3G network!"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by stardustdk on 2008-01-23
Hey all.

I have happily used my 3G network with Ubuntu 7.10 but after having installed what i want and need, i suddenly have no more 3G network with my HUAWEI E220 USB modem?! It has worked flawlessly  since 1. October 2007.

I use Gnome-PPP and wvdial.

wvdial.conf looks like this: 

[Dialer 3]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
Phone = *99#
username=any
password=any
Stupid Mode = 1
Init3 = AT+CGDCONT=1,"IP","bredband.tre.dk"
Dial Attempts = 3

Best regards 

Stardustdk

.

---

### Post by PmDematagoda on 2008-01-23
Did you by any chance check if it was something with the network itself?

---

### Post by stardustdk on 2008-01-23
How do i check that?

Best regards

---

### Post by PmDematagoda on 2008-01-23
You can ask your network provider if there is a problem with the 3G connection at your place or tell them that your modem does not connect to the 3G network(This may not work if they do not support Linux, but is still worth a try;)).

---

### Post by stardustdk on 2008-01-23
When i try to start being online with wvdial, the respond is:

john@Duo2:~$ wvdial 3
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0
WvDial<*1>: Re-Sending: ATZ
WvDial<Err>: Modem not responding.


Not that much network problem...

Best regards

Stardustdk

---

### Post by Kevbert on 2008-01-23
The At commands you're using don't tell you whether there is a 3G network running or not.  The best way to check the network is to check with another 3G phone.  By the look of it, you're dialing at least a GPRS network.  If you can get your hands on another 3G phone that would probably help to compare the two.  Another thing is that when the network is busy you may loose 3G due to the amount of traffic (i.e. phone calls) on the network.
It may be worth checking your providers web page as they may have changed the APN  (bredband.tre.dk) in your case.
Good luck.

---

