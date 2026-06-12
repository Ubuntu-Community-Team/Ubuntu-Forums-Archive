---
title: "Configuration does not specify a valid phone number"
date: 2009-07-03
forum: Hardware
---

### Post by twotool on 2009-07-03
I am using Ubuntu 9.04 desktop version. I want to use Teltonika T-Modem USB to access internet. So I have edited wvdial.conf as below 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 A0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","blweb"
Modem Type USB Modem
Phone = *99#
ISDN = 0
Password = ' '
New PPPD = yes
Username = ' '
Modem = /dev/ttyUSB0
Baud = 230400
Stupid Mode = yes
Carrier Check = no

but it says something like this

--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

My subscriber did not provide me any User name/password.
Please help me as what to do. My current location is Bangladesh.

---

### Post by GeorgeVita on 2009-07-04
Hi **twotool**,
I think you are dialling using a different wvdial.conf than that you have edited!

> --> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.


From above the Init3 line is missing!

Your configuration file must be **/etc/wvdial.conf**
You can check it: **cat /etc/wvdial.conf**
and edit it: **sudo gedit /etc/wvdial.conf**

Regards,
George

---

### Post by twotool on 2009-07-05
> **twotool said:**
> I am using Ubuntu 9.04 desktop version. I want to use Teltonika T-Modem USB to access internet. So I have edited wvdial.conf as below 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 A0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","blweb"
Modem Type USB Modem
Phone = *99#
ISDN = 0
Password = ' '
New PPPD = yes
Username = ' '
Modem = /dev/ttyUSB0
Baud = 230400
Stupid Mode = yes
Carrier Check = no

but it says something like this

--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

My subscriber did not provide me any User name/password.
Please help me as what to do. My current location is Bangladesh.
Dear Gorge,
Thanks a lot. It worked for me.
Warm regards, Twotool.

---

