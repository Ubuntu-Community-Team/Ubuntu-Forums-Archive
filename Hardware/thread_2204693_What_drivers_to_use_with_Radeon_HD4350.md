---
title: "What drivers to use with Radeon HD4350?"
date: 2014-02-09
forum: Hardware
---

### Post by Anatoliy_Dinis on 2014-02-09
Installed 12.04.3 and no graphics driver installed, running sssllllloowwww. The catalyst won't install cuz of xorg 1.13, any suggestions?

---

### Post by Bashing-om on 2014-02-09
Anatoliy_Dinis; Hi ! Welcome to the forum .

It is a sad tale I tell:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)


So, the recommended thing is open source graphics driver for releases after 12.04.1 .
If the proprietary drivers is required, then install release 12.04.1. - that is LTS, and has support 'till 2017 -

[INDENT][INDENT]somethings are beyond our control
[/INDENT][/INDENT]

---

### Post by jp734 on 2014-02-09
radeon drivers will work just fine. As mentioned above, fglrx will not work with your card.

---

### Post by Mark Phelps on 2014-02-09
> no graphics driver installed, running sssllllloowwww. 

IF there was no graphics driver, then you would be presented with a blank, black screen.  Presuming that you are getting to working desktop, then  there MUST be a graphics driver present.

Unfortunately, as the quote from a previous post of mine indicated, there are no fglrx drivers that will work with your card and any Ubuntu newer than 12.04.1.

I've been using the default Radeon drivers on an HD 4290 and have seen no degradation in performance over that of the fglrx drivers.

So, if the overall machine performance is s...l...o...w, it is not the graphics driver that is to blame.

---

### Post by mastablasta on 2014-02-10
4350 could be mobile chip....

try 14.04 - i believe it hit beta and should have new kernel & better opensource drivers.

---

### Post by Anatoliy_Dinis on 2014-02-10
right. I've tried 12.04.03, and 12.04.4 and I've also downloaded 12.04.1 and 12.04. (to try the catalyst with old kernel and xorg)
but when I installed 12.04.1 and boot on GruB it says the version is 12.04.2...wierd.


After installing Ubuntu I got to System Settings >> Details >> Graphics
it says no driver: none experience: standard

But as far as the open source drivers go I'm having difficutly installig them. Every time I install xserver-xorg-core and restart my screen is black.
Any suggestions how to install them properly? thanks

---

### Post by QIII on 2014-02-10
Hello!  The open source Radeon driver is installed by default in the Linux kernel when you install Ubuntu.  There is nothing more to install.

Disregard the message that there is no driver installed or in use.  There is no *proprietary *driver installed.

As mentioned before, your performance issues may be entirely unrelated to the Radeon driver.

---

### Post by Anatoliy_Dinis on 2014-02-11
Ok thanks. I'll dig through the forums and Try to figure out why my setup so slow

---

### Post by Yellow Pasque on 2014-02-11
Post your /var/log/Xorg.0.log file. Use [ code ][ /code ] tags ...

> After installing Ubuntu I got to System Settings >> Details >> Graphics
it says no driver: none experience: standard
Install mesa-utils and that should resolve itself. [https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

---

