---
title: "Cant get internet connection with kppp"
date: 2005-11-19
forum: General Help
---

### Post by drolyk on 2005-11-19
Hi All!
I want to ask about GPRS connection setup with kppp. Here are my steps in detail:

1) drolyk@c3po:~$ hcitool scan
Scanning ...
        00:14:A7:57:B2:9C       R2
2) rfcomm bind 0 00:14:A7:57:B2:9C 1
3) Some kppp setup, I change second initialization command, set modem device to /dev/rfcomm0, add fone namber, etc. But when I`m trying to connect pppd dies with error 10 

The most strange thing is that I can connect to internet with wvdial :) with such config:
[Dialer Defaults]
Modem = /dev/rfcomm0
Baud = 115200
Init1 = ATZ
Init2 = AT+CGDCONT=1,"IP","internet.mc"
Phone = *99***1#
# user and pass are not important
Username = megafon
Password = megafon

Thanks

---

