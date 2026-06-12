---
title: "Radeon 9250"
date: 2008-08-16
forum: General Help
---

### Post by The System on 2008-08-16
Okay first off, i'm new here. I just started using Xubuntu, after using Fedora Gnome for a while. Any way, i searched every where on how to install the radeon 9250 drivers on Ubuntu/xubuntu, and what ever i found either didn't work, or some parts made no sense(When i typed what it said into the shell, something different would come up). So before you start telling me to search more, or i didn't look good enough, can some one just send a me link to a site that actually shows you how to install the drivers for Xubuntu?

By the way, my computer is only 2 - 3 years old, i just like XFCE

EDIT : Almost forgot, i'm running 8.04

---

### Post by The System on 2008-08-24
SOrry for bump guys, but it's been a week, any help?

---

### Post by philetus on 2008-08-24
I searched also.There doesn't seem to be drivers for the Radeon 9250 for W2k, so I'm pretty sure ATI hasn't made any for Linux.

---

### Post by nickgaydos on 2008-08-24
Try using EnvyNG for your drivers.
> sudo apt-get install envyng-gtk

---

### Post by nickgaydos on 2008-08-24
> **philetus said:**
> I searched also.There doesn't seem to be drivers for the Radeon 9250 for W2k, so I'm pretty sure ATI hasn't made any for Linux.

If your trying to use an ATI card for Windows and your manufacturer doesn't support your operating system, use Omega Drivers (Google is your friend).

---

### Post by Catalyst2Death on 2008-08-24
well... You could try the Restricted drivers:
System>Administration>Hardware Drivers and then check enable, restart when prompted.

There is also the proprietary ATI drivers:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

and finally you could play roulette with you xorg.conf...
```

sudo cp /etc/X11/xorg.conf{.back} #creates xorg.conf.back in that folder
sudo nano /etc/X11/xorg.conf
```

Find Device and change the Driver line to "ati", "radeon" or if the proprietary driver is installed "fglrx"  If everything really goes to hell, then you can put "vesa" in as a temporary solution to get back to a gui

Edit: Didn't see that there may not be support for your card... I wouldn't try the proprietary drivers unless I was feeling frisky... Playing with xorg.conf might work...

---

