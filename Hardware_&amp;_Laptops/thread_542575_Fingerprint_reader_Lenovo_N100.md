---
title: "Fingerprint reader Lenovo N100"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by mateCH on 2007-09-04
Dear all

First of all I'm a very happy Ubuntu user :) :) since 1/2 year and wouldn't get something other. 
Okay for Skype I use my dual boot system W....., but just for this one.
I've installed Feisty 7.04 on my N100. Basically most of the things are working, this means card reader, sound, web cam, screen solution. 
Actually I'm trying to install the fingerprint reader. Therefore I've found a deb file. Everything installed fine. If I tried to login with root in terminal it comes a fault.

root@wenmar-laptop:/home/wenmar# tf-tool --acquire

ThinkFinger 0.3 ([http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/))
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...USB device not found.

I've also checked the link as follows and the same fault.
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader")

Does anybody know if there is a possibility to connect the USB device? 
If I check with lsusb then I get the following:

wenmar@wenmar-laptop:~$ lsusb
Bus 005 Device 003: ID 0c45:624f Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0a5c:2101 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

Is there the fingerprint reader as AuthenTec?

Any ideas? 

Thx in advance

---

### Post by aNoble on 2007-10-25
I have an N100 too.

Last I checked, thinkfinger didn't work for Authentec scanners.

The closest I've come to getting the fingerprint scanner to work is this. [http://www.ag-networking.com/](http://www.ag-networking.com/)

You can get a fingerprint image with it but it's not tied into any authentication methods.

---

