---
title: "ubuntu 12.04 not detecting radeon 9800xt"
date: 2012-06-16
forum: Hardware
---

### Post by Matt26 on 2012-06-16
i've noticed that ubuntu 12.04 doesn't seem to detect my radeon 9800xt video card properly- it shows up as 'unkown' for the Graphics section of the system details.

is there any way that i can get ubuntu to recognize this video card?

thanks!

---

### Post by N0oki3 on 2012-06-16
Hello there. Here you can check hardware[compactibility ](http://wiki.cchtml.com/index.php/Hardware)

and [how to install drivers](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

**note**: Check which version of catalyst center supports your graphic. So you won't install better 1

---

### Post by QIII on 2012-06-16
Your card is not supported by ATI's current Linux driver and the legacy driver will not work with X server versions since 2008.

Just continue with the open source driver, which will work very well.

---

### Post by Matt26 on 2012-06-17
> **QIII said:**
> Your card is not supported by ATI's current Linux driver and the legacy driver will not work with X server versions since 2008.

Just continue with the open source driver, which will work very well.

thanks- is the open source driver used as the default when ubuntu is installed or do i have to install it manually?

---

### Post by Yellow Pasque on 2012-06-18
The 'unknown' thing is a common bug with the sysinfo program. Don't worry about it (the best driver setup for your card is used as the default).

---

### Post by Matt26 on 2012-06-19
i was looking for some information and came across these pages.

do these refer to the same open source/default driver that was mentioned in this thread?

[http://manpages.ubuntu.com/manpages/precise/man4/radeon.4.html]("http://manpages.ubuntu.com/manpages/precise/man4/radeon.4.html")

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

thanks!

---

### Post by Yellow Pasque on 2012-06-19
> **Matt26 said:**
> do these refer to the same open source/default driver that was mentioned in this thread?

Yes

---

