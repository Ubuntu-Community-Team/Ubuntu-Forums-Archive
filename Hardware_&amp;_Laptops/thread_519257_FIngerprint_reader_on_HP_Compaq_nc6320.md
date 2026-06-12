---
title: "FIngerprint reader on HP Compaq nc6320"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by slasherx2 on 2007-08-06
Hi there.

I was wondering if anyone else has one of these laptops (or anyone else with any ideas) with the fingerprint reader working could give me a helping hand getting mine to work please?

I followed a wiki on how to install thinkfinger and got that installed and everything but now for some reason when I try to acquire a reading it comes up 

```
craig@craig-laptop:~/thinkfinger-0.3$ sudo tf-tool --acquire

ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...USB device not found.

```

Here is my lsusb if that helps

```
craig@craig-laptop:~/thinkfinger-0.3$ lsusb
Bus 005 Device 004: ID 08ff:2580 AuthenTec, Inc. 
Bus 005 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 005 Device 002: ID 0424:2503 Standard Microsystems Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

I think the top one is the fingerprint reader.

Any help would be appreciated, I'm not even sure if it's possible to get it to work (if not I'll have to bug HP Compaq)

Thanks in advance

-Craig (Slasherx2)

---

### Post by Vermind on 2007-09-20
Hello, I have a HP Pavilion dv6000 with the same usb id for the fingerprint reader. I am looking into getting it working now. Will post discoveries here.

```
vermind@periptero ~ $ lsusb 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 064e:a101 Suyin Corp. 
```

---

### Post by Vermind on 2007-09-20
The AES 2501 driver recognizes the hardware. I do not have time to try it now, but here are a few useful links:
[https://wiki.ubuntu.com/FingerprintAuthentication](https://wiki.ubuntu.com/FingerprintAuthentication) Generic information about fingerprinting and useful links
[http://home.gna.org/aes2501/index_en.html](http://home.gna.org/aes2501/index_en.html) developer of the free driver
[http://www.qrivy.net/~michael/blua/](http://www.qrivy.net/~michael/blua/) bioapi developer
[http://code.google.com/p/bioapi-linux/downloads/list](http://code.google.com/p/bioapi-linux/downloads/list) bioapi now hosted by google
[http://code.google.com/p/pam-bioapi/](http://code.google.com/p/pam-bioapi/) the pam stuff for bioapi

With bioapi and the AES 2501 driver, I guess it would be possible to make this work.

---

### Post by Vermind on 2007-09-20
News so far:
The bioapi and pam-bioapi and biometrics-manager compile ok, with some tweaking.
The aespack (the "unfinished" stuff) contains some typos which I had to fix to compile it on my 64-bit laptop. The "biologin" has a typo: 
```
calc_vield  should be calc_vfield
```
. The enroll app is escaping "/" needlessly. This does not cause building it to fail, so I guess it does not matter.
The usbrunner in the enroll directory records xpm images of Your finger. Seems to work by itself.
The biologin thing crashes at first; but from the code I can see that it is trying to read a file called /etc/fps/users and seek in there without checking it exists. I created an empty file there and it stopped crashing, but I get no interesting output. It is trying to compare the image to something in that file; I will try and find out later what.

The aes stuff compiled earlier is not found by the bioapi; the BioApiTest program gives me errors.
 I'm not sure if it should be recognized at this point. I put the LibAES2501.so to /usr/lib and modified the config file at /etc/bioapi/birdb.conf to have the path to the module, to no avail.

Do NOT use the free aes2501 driver with the "aespack", it will cause empty scans and generally bad behaviour of the aespack stuff.

---

### Post by Vermind on 2007-09-20
Ok, the biologin looks for 
```
/etc/fps/users
```
which should contain usernames.
Based on the username, it looks for
```
/etc/fps/username.xpm
```
And then would compare it to the xpm it reads,
if the comparison was implemented.
The comparison functions are empty; so we can do nothing
until someone writes some more code; at least not with this driver.
I will look into the other driver alternatives.

---

### Post by cowkiller on 2007-09-23
I'm having the same problem with a HP pavilion dv2570, having not any good result with the howtos and drivers mentioned here. 
Here's my lsusb output

```
Bus 007 Device 004: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 04f3:0210 Elan Microelectronics Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0e8f:0003  
Bus 003 Device 001: ID 0000:0000  

```

so here's the same authentec fingerprint. 
I hope to have any solution soon. I've heard about [Bio-ReVS]("http://youtube.com/watch?v=NzXWVoBN1kI") but it's still unreleased... seems that nothing's good to make it work so far :confused:

---

### Post by lucidd on 2007-12-04
...

---

### Post by Vermind on 2008-03-26
News: I got the reader working, even for PAM login, with:
[http://reactivated.net/fprint/wiki/Main_Page](http://reactivated.net/fprint/wiki/Main_Page)
But the problem is that my reader does not recognize my finger! No two scans are the same. Seems like that fprint should add a lot of image recognition logic to work with my reader's driver.

---

