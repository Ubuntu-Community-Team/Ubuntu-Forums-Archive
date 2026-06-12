---
title: "Problem with wvdial and pppd"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by Alsvartr on 2007-12-29
Hi. I have a laptop with ubuntu 7.10 and trying to connect to gprs via my mobile phone (Samsung SGH-i700), but got this problem:
```
sudo wvdial defaults
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet.beeline.ru"
AT+CGDCONT=1,"IP","internet.beeline.ru"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Dec 29 09:22:09 2007
--> Pid of pppd: 23074
--> Using interface ppp0
--> pppd: &#65533;[03][06][08]&#65533;[03][06][08]
--> pppd: &#65533;[03][06][08]&#65533;[03][06][08]
--> pppd: &#65533;[03][06][08]&#65533;[03][06][08]
--> pppd: &#65533;[03][06][08]&#65533;[03][06][08]
--> pppd: &#65533;[03][06][08]&#65533;[03][06][08]
--> Disconnecting at Sat Dec 29 09:22:40 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```

tail -f /var/log/messages:
```
Dec 29 09:21:53 localhost kernel: usb 1-2: new full speed USB device using ohci_hcd and address 34
Dec 29 09:22:03 localhost kernel: usb 1-2: configuration #1 chosen from 1 choiceDec 29 09:22:03 localhost kernel: cdc_acm 1-2:1.0: ttyACM0: USB ACM device
Dec 29 09:22:09 localhost pppd[23074]: pppd 2.4.4 started by root, uid 0
Dec 29 09:22:09 localhost pppd[23074]: Using interface ppp0
Dec 29 09:22:09 localhost pppd[23074]: Connect: ppp0 <--> /dev/ttyACM0
Dec 29 09:22:39 localhost pppd[23074]: LCP: timeout sending Config-Requests
Dec 29 09:22:39 localhost pppd[23074]: Connection terminated.
Dec 29 09:22:39 localhost pppd[23074]: Modem hangup
Dec 29 09:22:39 localhost pppd[23074]: Exit.

```

/etc/wvdial.conf:
> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
INIT5 = AT+CGDCONT=1,"IP","internet.beeline.ru"
Modem Type = Analog Modem
ISDN = 0
Phone = *99***1#
Modem = /dev/ttyACM0
Username = beeline
Password = beeline
Baud = 57600
Stupid Mode = on
Carrier Check = no

---

### Post by parames on 2008-06-11
Hi,

 I am getting the same error mentioned above. does anybody have any idea.. i am using Samsung E840

Looking for positive result

---

