---
title: "Troubles establishing connection with wvdial"
date: 2014-01-20
forum: Hardware
---

### Post by reggler on 2014-01-20
I have a Huawei cell modem EM680 with which I can establish a connection on my Ubuntu 13.10 box just fine. I plug it in and I can establish a connection using the Connections Manager.

I have a box without X server (running embedded Debian) and I want to establish a connection with that same modem on that box. I can get a serial link at /dev/ttyUSB1 and if I connect to it using screen /dev/ttyUSB1 460800 and send AT, it responds with OK just fine &#8212; so the modem works! Ater that I tried to establish a connection using wvdial with my /etc/wvdial.conf configured like this:
```
[Dialer Defaults]
Init1 = ATZ
Init2 = AT+CFUN=1
Init3 = AT+CGDCONT=1,"IP","m2mstatic.apn"
Modem = /dev/ttyUSB1
Phone = *99***1#
Modem Type = USB Modem 
Username = "blank"
Password = "blank"
Stupid Mode = yes
New PPPD = yes
Baud = 460800
ISDN = 0
```
I tried to launch wvdial without any options or with wvdial eap-interval 1 require-chap because in my Connection Manager window, under the tab PPP following checkboxes are checked: EAP, MSCHAP, PAP, MSCHAPv2, CHAP, Use BSD data compression, Use Deflate data compression and Use TCP header compression. But upon launch I just get
```
# wvdial eap-interval 1 require-chap
--> WvDial: Internet dialer version 1.61
--> Warning: section [Dialer eap-interval] does not exist in wvdial.conf.
--> Warning: section [Dialer 1] does not exist in wvdial.conf.
--> Warning: section [Dialer require-chap] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+CFUN=1
AT+CFUN=1
OK

--> Sending: AT+CGDCONT=1,"IP","m2mstatic.apn"
AT+CGDCONT=1,"IP","m2mstatic.apn"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT 14000000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Jan 22 03:26:56 2007
--> Pid of pppd: 4295
```
Here it waits for a about a minute and then:
```
--> pppd: H&#65533;[02]
--> pppd: H&#65533;[02]
--> Disconnecting at Mon Jan 22 03:27:57 2007
--> The PPP daemon has died: Connect script failed (exit code = 8)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
--> Disconnecting at Mon Jan 22 03:28:19 2007
#
```
but I can never actually reach the internet. Exit code 8 in the pppd man page says: The serial port could not be opened. &#8212; which is ridiculous as I just opened (and closed(!) it with screen). Any ideas where I'm going wrong or what I'm missing? :?:

**edit**

I just found the connection manager's config file and it looks like this, that might help too, hey?:
```

[connection]
id=Rogers
uuid=5c4ed6f8-9ece-4888-a129-65ed5c741502
type=gsm
permissions=user:ron:;

[gsm]
number=*99#
password-flags=1
apn=m2mstatic.apn
pin-flags=1

[ipv4]
method=auto

```

---

### Post by lkraemer on 2014-02-02
reggler,
I just posted on the Debian forum:   [http://forums.debian.net/viewtopic.php?f=7&t=110873&p=528647#p528647](http://forums.debian.net/viewtopic.php?f=7&t=110873&p=528647#p528647)

I think you need to follow that posting, and reply there too since it's the same information, and I replied there first.

Larry

---

