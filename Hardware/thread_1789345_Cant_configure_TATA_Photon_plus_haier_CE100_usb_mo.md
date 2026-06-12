---
title: "Cant configure TATA Photon plus haier CE100 usb modem in UBUNTU 9.10 &amp; also in 10.10"
date: 2011-06-23
forum: Hardware
---

### Post by surajit697 on 2011-06-23
[SIZE=2]I have got a TATA photon+ haier CE100 usb modem providing mobile broadband service...
It has default username and password 'internet' (both are same).
I have tried through Network connection manager... do not show any available connection... in my Desktop (which has Ubuntu 10.10) the modem didn't show any icon on the desktop... when I run wvdial, it says that the modem is not responding....
In the laptop (it has ubuntu 9.10, as it has only 256MB RAM, so I didn't upgrade it), the modem is detected, and after ejecting it (as suggested by some posts and also by the haier manual found on their site), when I run wvdial, it tries to connect for sometime and then shows a error message that the modem is not responding....


here is my wvdial.conf file...

[Dialer Defaults]
Init = ATZ
Init = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 115200
Modem = /dev/ttyUSB0
Phone = #777
Username = internet
Password = internet
stupid mode = 1


output of wvdial before ejecting the modem:
```
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
```output of wvdial after ejecting the modem:
```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&)'[7f][0c]}'}"}(}"K ~~[7f]}#@!}!}"} }9}"}&} } } } }#}%B#}%}%}&)'[7f][0c]}'}"}(}"[07]M~~[7f]}#@!}!}#} }9}"}&} } } } }#}%B#}%}%}&)'[7f][0c]}'}"}(}"C[16]~~[7f]}#@!}!}$} }9}"}&} } } } }#}%B#}%}%}&)'[7f][0c]}'}"}(}"}.}>~~[7f]}#@!}!}%} }9}"}&} } } } 
--> Timed out while dialing.  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
```I cant eject that modem from my desktop, as nothing is shown there in the desktop... so applying wvdial, it shows the same output as laptop.

Here is my lsusb output with attaching the modem.
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 201e:2009  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```[/SIZE]

---

### Post by surajit697 on 2011-06-25
I'm waiting for the reply.
Did I post on the wrong category? If so, inform me where to post.
:(

---

### Post by DL Moon on 2012-05-27
Did you ever get an answer to this? I'm having similar troubles with the same USB modem on 12.04.

---

### Post by surajit697 on 2012-05-28
I didn't get the answer of this post ever. But with the upgraded version  of ubuntu, I once was able to connect tata photon with UBUNTU. But that  was not the same modem I mentioned here, and also that connection was  made only once. I gave up with this.
But I think it is now easier as the usbmodswitch package is upgraded a  lot and I hope it will detect the modem in the network manager applet.  Though I am not sure that it will work fine or not. You mentioned that  you have problem with this modem on 12.04, so I think its not going to  work.
I once used Sakis3G, a well build shell script which is build to connect  a huge number of usb and bluetooth modems (such as phones and other usb  or bluetooth dongle). You can give it a try.

Here is the link of their website.
[http://www.sakis3g.org/](http://www.sakis3g.org/)

---

