---
title: "Compaq x1010 / ATI issues"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by kprowell on 2007-11-25
I have a Compaq Presario x1010us laptop that has an ATI Mobility 9200 graphics card. In previous versions of Ubuntu (even up to Fiesty) the ATI card was able to use Compiz / Desktop Effects. Now with Gutsy, I cannot get it to work. I've tried Envy but it didn't work. It stopped saying something about the proprietary driver is installed. I'm stuck. If anyone out there with this laptop and or video card got it to work please share your solution.
 
As a side note, I tried openSuse 10.3 and it worked there but I really don't like that distro and or RPM based distros.
 
Thanks in advance.

---

### Post by Yellow Pasque on 2007-11-25
ATI dropped support for the Radeon 9200 and lower from their latest drivers.
The only thing I can think of besides the open-source ati driver is to try an older version. Here's the link to the deb package that came with edgy. You could try installing that.
[http://packages.ubuntu.com/edgy/misc/xorg-driver-fglrx](http://packages.ubuntu.com/edgy/misc/xorg-driver-fglrx)

---

### Post by kprowell on 2007-11-25
Thanks Temüjin.
 
Two things.  I am still new at this so...  Is it possible to use the older version (1)?  Where do I get the open source driver?  I looked before (and maybe I just missed it) and didn't find it.  Do I have uninstall anything before installing the open source driver (2)?
 
-Kevin

---

