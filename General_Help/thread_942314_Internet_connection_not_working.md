---
title: "Internet connection not working"
date: 2008-10-09
forum: General Help
---

### Post by ehsensiraj on 2008-10-09
I am using Huawei ETS 2051 Fixed Wireless Terminal. Here is my wvdial.conf

> [Dialer ptcl]

Modem = /dev/ttyUSB0

Baud = 230400

Phone = #777

Init1 = ATZ

Stupid Mode = 1

Dial Command = ATDT

Username = [email]vwireless@ptcl.com[/email]

Password = ptcl

PPPD Options = crtcts multilink usepeerdns lock defaultroute

But when I enter this command " wvdial ptcl". Terminal just show the following result but didn't connect to my ISP.

> --> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
OK
--> Re-Sending: ATZ
OK
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK


can you please tell me what I am missing.

---

### Post by roger_1960 on 2008-10-09
Hi

Perhaps this will help - depends if you understand it!!!


[http://ubuntuforums.org/showthread.php?t=464779](http://ubuntuforums.org/showthread.php?t=464779)

---

### Post by ehsensiraj on 2008-10-10
I guess thats what I exactly did to setup my connection. Well I check it again. by the way thanks for your help.

---

