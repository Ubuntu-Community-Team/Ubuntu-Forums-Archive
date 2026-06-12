---
title: "Dialing to airtel gprs"
date: 2008-12-01
forum: Hardware
---

### Post by vivekrocks on 2008-12-01
I have installed Ubuntu 8.04 Hardy on HP6720s Compaq. Following is the configuration:

RAM: 1 GB
CPU: 1.4GHz Intel centrino Core 2 duo
HDD: 160 GB SATA

I got a sony ericsson w200i with a modem. i am trying to dial to Airtel subscriber using GPRS. The tool that I am using is wvdial

Following is my wvdial.conf file :
```
[Modem0]
Modem = /dev/rfcomm0
Baud = 230400
SetVolume = 0
DialCommand = ATDT
FlowControl = Hardware(CRTSCTS)
[Modem1]
Modem = /dev/ttyACM0
Baud = 230400
SetVolume = 0
DialCommand = ATDT
FlowControl = Hardware(CRTSCTS)
[Dialer GPRS]
Username = <>
Password = <>
Phone = *99***1#
Mode = 1
Inherits = Modem0
[Dialer DATA]
Username = <>
Password = <>
Phone = *99***1#
Mode = 1
Inherits = Modem1
[Dialer Defaults]
Modem = /dev/rfcomm0
Baud = 230400
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"
ISDN = 0
Modem Type = Analog Modem
Area Code =
Phone = *99***1#
Username = <>
Password = <>
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Force Address =
Idle Seconds = 3600
DialMessage1 =
DialMessage2 =
ISDN = 0
Auto DNS = 1 
```

Whn i dial using :

```
wvdial
```

I get connected but i cant surf the internet. I set the proxy settings to direct connection. Still i cant surf over it!! Can some one tell me what might be the problem? and probably, how to solve it? :(

---

### Post by me.anandvivek on 2009-03-12
R u sure u're using ur correct config settings number..???The no. u're dialin should correspond to the no. of ur config setting

---

### Post by shailendra on 2009-03-12
Please refer to the HOW TO at [http://ubuntuforums.org/showthread.php?t=1091189](http://ubuntuforums.org/showthread.php?t=1091189)

Hope it helps you.

---

### Post by sahabcse on 2009-03-12
Hi

Install ubuntu 8.10 version It will automatically detect airtel gprs

---

