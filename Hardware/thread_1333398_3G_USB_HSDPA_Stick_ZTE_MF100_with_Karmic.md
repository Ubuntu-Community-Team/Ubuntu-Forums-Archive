---
title: "3G USB HSDPA Stick ZTE MF100 with Karmic?"
date: 2009-11-21
forum: Hardware
---

### Post by chloraldo on 2009-11-21
Hi all

I am running Jaunty with a ZTE MF100 USB Stick. It was quite a hassle to get it running (modeswitch) and now I'm wondering if I can upgrade to Karmic 9.10 and run the ZTE modem the same way. Any experiences?

Thanks for your advice!

---

### Post by KumBa on 2009-11-21
Unfortunately no good luck for me.
Worked fine with 8.4 till 9.04 (usb-modeswitch + ZTE MF636), but now with 9.10 it is not recognised.

---

### Post by danpos on 2009-11-21
@All

Hi guys! One brazilian member from ubuntuforum-br.org posted that (he just upgraded to Ubuntu 9.10) that using this version of usb-modemswitch ([usb-modeswitch_0.9.7_i386.deb](https://forge.betavine.net/frs/download.php/490/usb-modeswitch_0.9.7_i386.deb)) did the trick for him (supposing that your installation be 32 bits); also I would suggest to install this other package ([ozerocdoff_0.4-2_i386.deb](https://forge.betavine.net/frs/download.php/538/ozerocdoff_0.4-2_i386.deb)).

Here in my Ubuntu 9.04 these packages did the trick (I'm posting using the 3G - HSDPA - connection from my ZTE MF100 modem ;) ).

Let me know if this tip worked for you.

Lucky,

Danpos.

---

### Post by gabello on 2009-12-13
How am I suppose to use usb-modeswitch_0.9.7_i386 and ozerocdoff_0.4-2_i386 for the zte mf110 in ubuntu 9.10?

---

### Post by gradinaruvasile on 2009-12-13
With the Vodafone Mobile Connect application maybe?

[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

---

### Post by gabello on 2009-12-13
Thank you, but I presume that is a specific application for vodafone 3G services?

---

### Post by Paulo Wageck on 2009-12-19
[http://ubuntuforums.org/showthread.php?t=1359410](http://ubuntuforums.org/showthread.php?t=1359410)

The thread above is about my experinece with this problem (solved). 

I hope it helps!

Cheers!

---

### Post by gabello on 2009-12-19
Creating a ZTE.rules file in /etc/udev/rules.d with the following:

```
SYSFS{idVendor}=="19d2",*SYSFS{idProduct}=="2000",*RUN+="/usr/bin/eject*%k",*OPTIONS+="last_rule"
```


should change lsusb of modem from 19d2:2000 (cd-rom) to the correct modem code.

---

