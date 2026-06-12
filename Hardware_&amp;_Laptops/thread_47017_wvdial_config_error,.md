---
title: "wvdial config error,"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by kye on 2005-07-07
Hi Guys,

Im trying to get my external modem to dial, it gets auto detected ok I run pppconfig and set it up, I see it apear in the list system config, networking program, the check mark on the side of it in the list apears for about 2 seconds then disapears, I try and dial from the wvdial program and I get this:

user@ubuntu:~ $ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0L3
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0L3
ERROR
--> Bad init string.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0L3
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0L3
ERROR
--> Bad init string.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0L3
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0L3
ERROR
--> Bad init string.

Does anyone have any idea whats going on here.

Do I need to install some drivers? for this internal modem.


Kye

---

