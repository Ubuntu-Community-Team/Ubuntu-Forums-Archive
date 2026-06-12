---
title: "Hollywood+ (dxr3) + My Media System"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by tommi-fi on 2007-06-02
Hello,

I'm having problems getting Hollywood+ MPEG decoder card to work. I have installed em8300 drivers using apt-get (apt-get install em8300) all four packages that relates to it.

```
htpc:/usr/local/src/mms/mms-1.0.9$ ./mms
Config: Opening configuration file /etc/mms/config
Using /etc/mms/ as configuration directory
DXR3: Could not open device/dev/em8300_mv-0
```

That is what I get when trying to start mms.

Computer is a Fujitsu ErgoPro X with 256M RAM, 10Gt HD and 450MHz P3 Katmai running at 300MHz. Don't know how to get it to full speed.
I have Ubuntu 7.04 Server installed, no X.
[http://mms.kicks-***.org/wiki/index.php/Installation_on_Dapper](http://mms.kicks-***.org/wiki/index.php/Installation_on_Dapper) 
Forum software seems to edit link. a**

---

### Post by tommi-fi on 2007-06-03
When I try to load em8300 module ```
sudo modprobe em8300
``` I get error ```
module adv717x not found
``` What is this adv717x module and where do I get it.

---

### Post by altariel on 2007-09-22
I have exaclty the same problem! and the same question because of that ... :confused:
edit: the problem with adv717x not found I mean!

---

### Post by tohtoriS on 2007-09-22
Same here. Just tried installing the card and the driver, but same error message... Not too much information around the web about installing these cards on Ubuntu. :(

---

### Post by Bubbel on 2008-05-31
Same thing here. Found out that the /etc/modprobe.d/em8300 referred to the adv717x module, as well as the /etc/modutils/em8300 file.
Since adv7170 and adv7175 are present (check by doing modprobe -l|grep adv717), I assume i can replace the x with one of those.
First off: try to check wich one is loaded by using lsmod|grep adv717
This returns the adv7175 module for me.
Added the following line to the /etc/modprobe/aliases file:
[HTML]alias adv717x adv7175[/HTML]
Error message is gone, but now i have another. Trying to get more info at this site:
[http://dxr3.sourceforge.net/]("http://dxr3.sourceforge.net/")

I'll keep you informed.:popcorn:

Edit: Look [Here]("http://ubuntuforums.org/showthread.php?p=5084282") to see some explanation: http://ubuntuforums.org/showthread.php?p=5084282

:-? Bubbel

---

