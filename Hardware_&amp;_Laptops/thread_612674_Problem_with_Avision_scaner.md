---
title: "Problem with Avision scaner"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by Mangas on 2007-11-14
I have Avision AV600U scaner. But I can't use it. I'm using Ubuntu 7.10.  Below is the result of typing "lsusb":

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c312 Logitech, Inc. 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0638:0a13 Avision, Inc. 
Bus 001 Device 001: ID 0000:0000  

Avision is visible, but Xsane and Kooka can't find the scaner. 

Is there any way to force it to work?

Sorry for my terrible english.

---

### Post by linuxwizard on 2007-11-15
According to this that scanner Status  good 
[COLOR="Red"]good[/COLOR] means the device is usable for day-to-day work. Some rather exotic features may be missing
[http://www.sane-project.org/sane-mfgs.html#Z-AVISION](http://www.sane-project.org/sane-mfgs.html#Z-AVISION)

You do have Sane installed ?
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo) 

Here is a manpage from Sane; Look over for setup/configuration.
[http://www.sane-project.org/man/sane-avision.5.html](http://www.sane-project.org/man/sane-avision.5.html)

---

