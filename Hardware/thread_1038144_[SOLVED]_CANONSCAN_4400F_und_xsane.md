---
title: "[SOLVED] CANONSCAN 4400F und xsane"
date: 2009-01-12
forum: Hardware
---

### Post by jarbo on 2009-01-12
Got a new Canoscan 4400F, searching the forum, searching xsane getting xsane-0.996 and trying to make it usable as a packet with the debian-packet-manager. This is just the first test for adding xsane.org as a third source for the packet-list. So just the maybe simple question now:
Can anybody tell me the exact spelling of the apt-line???????
:confused:

thanks so far......

so I had a look at the hcl (lists for compatibility) by xsane and indeed this canon-model is not supported. But when I put on an epson V300 there is the same "no device found" message, not only xsane, though it shoud be supported. Now I found out to get iscan but I still cant get it work, the only thing that I found was an package that is meant for opensuse 10 anything. And the so called "alien" is just working with binary files. Any hints how to get iscan probably working?

---

### Post by groovete on 2009-01-12
Hi!
In my opinion you  can't use your scanner with Ubuntu. Have a look to this (german) site: [http://wiki.ubuntuusers.de/Hardware_blacklist](http://wiki.ubuntuusers.de/Hardware_blacklist)
 
Concerning xsane:
xsane is in the Ubuntu repository, so you don't need another source for it. There is no possibility to use xsane.org as a source for the Ubuntu packet-manager.

---

### Post by albinootje on 2009-01-12
> **groovete said:**
>  In my opinion you  can't use your scanner with Ubuntu. Have a look to this (german) site: [http://wiki.ubuntuusers.de/Hardware_blacklist](http://wiki.ubuntuusers.de/Hardware_blacklist)


Indeed.

But though unsupported by the Sane project :
[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

> 
CanoScan 4400F 	USB 	0x04a9/0x2228 	Unsupported 	GL841 based, to be added to genesys backend 	unsupported
(2007-01-28) 	?

It says at least "to be added to genesys backend", which gives a little bit of hope for the future.
You can also ask on the sane development mailinglist, perhaps some others are working on it, and you can contribute by testing development versions.

And also, you can try that scanner (usb ?) through VirtualBox with a MS-Windows guest VM on Linux.
At my work there's a HP scanner which is unsupported by Linux, but it worked inside VirtualBox on Linux.

---

### Post by patrickvdbemt on 2010-12-05
today running ubuntu 10.10
although scanner recognised with lsusb it cannot be found by scanner software
~$ lsusb
Bus 002 Device 004: ID 04a9:2228 Canon, Inc. CanoScan 4400F

---

### Post by almogabber on 2011-01-16
@patrickvdbemt hi, do you say that you solved the problem? I have the same scan, working with ubuntu10.10, and my pc recognizes it too with ~$lsusb. But now, how can I use the scan software? ianae.. 

Thanks!!

---

### Post by stuartmc on 2011-03-01
I have the same problem. System can recognise Canoscan 4400F but Xsane and simplescan cannot! Any help would be great thanks.

when I run lsusb the scanner is listed:
2Bus 001 Device 002: ID 04a9:2228 Canon, Inc. CanoScan 4400F"

---

### Post by mosaic2s on 2011-09-25
I am in the same boat.
have to manage with vbox.

---

