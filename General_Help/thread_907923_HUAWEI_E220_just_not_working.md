---
title: "HUAWEI E220 just not working"
date: 2008-09-02
forum: General Help
---

### Post by Athos101 on 2008-09-02
I have used the tips and stuff for getting it to work but I still have some problems that are preventing it from working.
I am on the Virgin Network in australia

I am running the coding 
[Dialer Default] 
Modem = /dev/ttyUSB0 
Baud = 460800 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0&C1 &D2 +FCLASS=0 
ISDN = 0 
Modem Type = USB Modem 
Phone = *99# 
Username = '' 
Password = '' 
Carrier Check = no 
Stupid Mode = yes

the HUAWEI set itself up automatically on windows so it does not have a username or password, also the Phone is the one that I found in the options of the virgin broadband Dial up window, but when I try and log on to the internet I get this.

--> WvDial: Internet dialer version 1.60 
--> Warning: section [Dialer default] does not exist in wvdial.conf. 
--> Cannot get information for serial port. 
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


So does anyone have any clues where I am going wrong and how I can fix them?

---

### Post by GeorgeVita on 2008-09-02
Hi,
from your post something seems to be wrong with the wvdial.conf

read the "Huawei e220 USB modem for beginners"
[http://ubuntuforums.org/showthread.php?t=843973](http://ubuntuforums.org/showthread.php?t=843973)

and my post
[http://forum.huawei.com/jive4/thread.jspa?threadID=322982&tstart=0&orderStr=9](http://forum.huawei.com/jive4/thread.jspa?threadID=322982&tstart=0&orderStr=9)

---

