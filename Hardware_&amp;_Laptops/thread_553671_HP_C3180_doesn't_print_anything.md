---
title: "HP C3180 doesn't print anything"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by kung fu buntu on 2007-09-18
I bought a HP C3180 and I'm unable to get it to print anything. 

I have CUPS installed as well as HPLIP. 
One thing that I'm unsure is the driver, I have a PPD file for HP C3100, but not a specific driver for C3180. 

I've trying adding the printer using kcontrol, hp-setup and CUPS web interface at [http://localhost:631](http://localhost:631) and it works fine until I get to the print test page phase... whereas it doesn't print anything!!! 

From /var/log/syslog 
Sep 18 02:50:29 stardust hpiod: unable to write data hp:/usb/Photosmart_C3100_series?serial=XXXXXXXX: Resource temporarily unavailable io/hpiod/channel.cpp 63 

Any suggestions? 
Thanks

---

### Post by linuxwizard on 2007-09-19
Run in a terminal window:  dpkg -l hplip

This checks and see what version HPLIP you are using. That printer requires min. version 1.6.6. You didn't post which version of Kubuntu you are using. That could be the issue why that printer is not showing in your list of printer drivers.

---

### Post by kung fu buntu on 2007-09-20
A reboot solved the problem... *windows style* :guitar:

But now I'm having problems with the margins :mad:
The problem is at a low level since even the test page isn't properly centered.
Any ideas?

---

### Post by linuxwizard on 2007-09-20
You should be able to go into your printer settings and the margins.

---

### Post by kung fu buntu on 2007-09-21
> **linuxwizard said:**
> You should be able to go into your printer settings and the margins.

I already tried that... but I couldn't find any setting for margins neither in CUPS nor in hp-toolbox.
I'm using HPLIP 1.6.10, which is the latest version in Debian testing.

---

### Post by kung fu buntu on 2007-09-22
Any ideas on this?

---

