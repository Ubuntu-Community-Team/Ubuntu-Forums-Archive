---
title: "nokia e71 as bluetooth modem"
date: 2008-10-04
forum: General Help
---

### Post by gimlithedwarf on 2008-10-04
I am seriously considering purchasing a nokia e71 and I was wondering if it is possible to use the phone as a bluetooth modem. Bluetooth works just fine on my laptop, so that isn't going to be an issue, but I was wondering if this is possible and how to get it working.

---

### Post by acorey on 2008-10-17
I just bought one and am posting this via cell modem.

I have a HP DV200 laptop and am using wvdial.

Just run wvdialconf as sudo. Then edit /etc/wvdial.conf

Mine looks like this (with tmobile data plan).

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 3600000
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
init3 = AT+CGDCONT=1,"IP","internet2.voicestream.com"
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = user
Password = pass
Stupid Mode = 1

It took a little searching around to get the config right, but it works well.

I love the phone. The google maps/gps overlay is awesome. Now to find some cool free symbian apps!

Hope this helps.

---

### Post by acorey on 2008-10-17
Also, you have to select sync mode instead of connect pc to internet when it pops up on the phone for some reason. otherwise it will not show up in lsusb.

Counterintuitive I know...

---

### Post by N3RVE_deact on 2009-07-03
Did any of you get this to work? The only reason why I still have Windows on my system is because I've been unable to accomplish this (Using my Nokia E71 as a 3G modem for Ubuntu Jaunty).

If anyone can post, step by step, what should be done to enable this, I'd be eternally grateful. 

This is the configuration data for my provider (MTN):

APN:          web.gprs.mtn.net
Username:     web
Password:     web
Phone IP:     Automatic
Proxy Server: 010.199.212.002
Proxy Port:   8080

When connecting using Windows Vista/7, the PC suite needs just the APN, username and password, not sure if ubuntu requires more.

Thank you for any help :)

---

### Post by lotvx on 2009-11-24
> **N3RVE said:**
> Did any of you get this to work? The only reason why I still have Windows on my system is because I've been unable to accomplish this (Using my Nokia E71 as a 3G modem for Ubuntu Jaunty).

If anyone can post, step by step, what should be done to enable this, I'd be eternally grateful. 

This is the configuration data for my provider (MTN):

APN:          web.gprs.mtn.net
Username:     web
Password:     web
Phone IP:     Automatic
Proxy Server: 010.199.212.002
Proxy Port:   8080

When connecting using Windows Vista/7, the PC suite needs just the APN, username and password, not sure if ubuntu requires more.

Thank you for any help :)

is this what  you need? I hope it helps

[http://ubuntuforums.org/showthread.php?t=1313882](http://ubuntuforums.org/showthread.php?t=1313882)

---

