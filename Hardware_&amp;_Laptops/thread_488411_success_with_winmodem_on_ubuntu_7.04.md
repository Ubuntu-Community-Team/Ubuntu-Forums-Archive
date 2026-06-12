---
title: "success with winmodem on ubuntu 7.04"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by hoggboy on 2007-06-30
:popcorn:  Finally had success getting internal modem winmodem to work on Toshiba Tecra 9000 laptop with ubuntu 7.04

Heres what i did.

1) Downloaded      sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb
and installed using package manager.

2) edited The /etc/wvdial.conf  to  look like this:

did sudo gedit /etc/wvdial.conf

[Dialer Defaults]
Dial Command = ATM1L3DT
Modem Type = Analog Modem
Baud = 115200
Carrier Check = on
;Minimize = off
Check Def Route = on
Abort on Busy = off
Abort on No Dialtone = on
Ask Password = off
Init = ATZ
Phone = ******************  put in your details
Username = **************
Password = *********
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +MS34
Init3 = AT+MS=34
Auto Reconnect = off
ISDN = 0
Auto DNS = on
Idle Seconds = 0
Stupid Mode = on
;Dock = off
Dial Attempts = 1
Modem = /dev/ttySL0

3) It would then daill out but not authenticate so did this,

edit /etc/ppp/options  *uncomment login*

Did sudo gedit /etc/ppp/options

# Use the system password database for authenticating the peer using
# PAP. Note: mgetty already provides this option. If this is specified
# then dialin from users using a script under Linux to fire up ppp wont work.
login 

4)Unticked wired connection in network settings and ticked modem * did not enable it*

now works with wvdial , also installed gnome ppp and seems to work just fine.

Hope this may help others.

---

### Post by Bartender on 2007-06-30
Thanks for sharing the results of your efforts!  I rarely hear of anyone making a laptop winmodem work...wonder how many Toshibas use the same winmodem chip?

---

