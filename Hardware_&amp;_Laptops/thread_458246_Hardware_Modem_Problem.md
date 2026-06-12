---
title: "Hardware Modem Problem"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by chager on 2007-05-29
I've installed Ubuntu 7.04 and I have a dial-up connection.  I've entered all my information.  I've selected ttyS0 for my port.  The modem dials but it never connects to my ISP.  Do I need to enter my IP address?  Any info is appreciated. :)

---

### Post by Mark_in_Hollywood on 2007-06-06
Do:

sudo wvdialconf

watch the responses and copy and paste the lines into a text file.

If wvdial found your modem and says everything is OK; do

sudo gedit /etc/wvdial.conf

remove the   ;

from in front of the lines and change the line order to

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Phone = 555-5555
New PPPD = yes
Modem = /dev/ttyS0
Username = your-name-here
Password = your-password-here
Baud = 115200

---

