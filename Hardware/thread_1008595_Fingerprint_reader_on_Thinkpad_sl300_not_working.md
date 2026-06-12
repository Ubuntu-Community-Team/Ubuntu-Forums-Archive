---
title: "Fingerprint reader on Thinkpad sl300 not working"
date: 2008-12-11
forum: Hardware
---

### Post by tjololo on 2008-12-11
Hi!
I have just bought a thinkpad sl300 (unfortunately with windows originally).
I have installed ubuntu 8.10, and it works like a charm, but I can't get the fingerprint reader to work with thinkfinger. I have tried multiple guides and howtoo's, but nothing seems to work:(
Here are the error message from tf-tool -acuire:
```
# tf-tool --acquire

ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...USB device not found.

```
It's the same both in usermode and rootmode.
Print from lsusb:
```

# lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 008: ID 0bdb:1900 Ericsson Business Mobile Networks BV 
Bus 008 Device 003: ID 17ef:480a Lenovo 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 147e:1000  
Bus 003 Device 002: ID 0a5c:2145 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
Any help would be nice:)

---

### Post by tjololo on 2008-12-12
Anybody?:P

---

### Post by iimre on 2008-12-13
Probably you have an UPEK fingerprint reader. Try this: " [http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation) "
I have in my Lenovo R61 an 147e:2016 UPEK reader. That works more or less with it.

---

### Post by tjololo on 2009-01-02
thanks, I have installed fprint by following the guide, but when I start the fprint fingerprint enroller the status is: no devices found.
Any other ideas?

---

### Post by UbuWu on 2009-01-03
The fingerprint reader on the sl300 is not supported by either thinkfinger or fprint yet. So besides waiting until one of them supports it there is not much you can do.

---

### Post by tjololo on 2009-01-05
Okay. Thanks for the answer:)

---

### Post by tjololo on 2009-06-04
Hi, again:)
I just wondered if there has been any updates regarding the fingerprint reader on my beloved sl300 ;)

---

### Post by cocolocko on 2009-06-10
> iimre  	
Re: Fingerprint reader on Thinkpad sl300 not working
Probably you have an UPEK fingerprint reader. Try this: " [http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation) "
I have in my Lenovo R61 an 147e:2016 UPEK reader. That works more or less with it. 

Works perfect for my Toshiba Tecra A9 with the Upek Fingerprint Reader:

ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader

Thanks

Greetings

---

### Post by mrfilgueira on 2010-07-22
This one should work on SL series with Upek readers:

[http://www.n-view.net/Appliance//fingerprint/index.php](http://www.n-view.net/Appliance//fingerprint/index.php)

Cheers!

---

