---
title: "Howto hear modem dial?"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by nab on 2006-06-24
Hi all,

I try to get my modem working and according to wvdail I either get an busy line or the line isn't answered.

So I want to hear what's going on, just to be sure what's going on.

I tried

> alsamixer -c1

to set the modemspeaker.

but everytime I start wvdail I reset the modespeaker to off. My wvdial.conf is:
> 
[Dialer Defaults]
Modem = /dev/ttySL0
Baud = 115200
Carrier check = no
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Dial Command = ATX0DT


[Dialer xxx]
Phone = XXX
Username = XXX
Password = XXX



The output after starting wvdail is:
> 
nab@box:~$ sudo wvdial test
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATX0DT01937400564
--> Waiting for carrier.
ATX0DT01937400564
BUSY
--> The line is busy. Trying again.


I'm working on an toshiba m30x-165 with an AC97-type winmodem.

Thanks for any help or link in advance!

---

### Post by guysmiley25 on 2007-06-20
Had any luck with this?

---

