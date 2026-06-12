---
title: "Driver for an HP dv9000 wireless card."
date: 2010-03-16
forum: Hardware
---

### Post by bigups43 on 2010-03-16
Hi there folks. I am utterly and completely new to Linux. I installed the newest version of Ubuntu, and Ive been a user for about 1 hour now. I am trying to find a driver for my hp9000's wireless card. I seem to be having no luck.

Any help would be much appreciated!

---

### Post by bigups43 on 2010-03-16
bump

---

### Post by howefield on 2010-03-16
Try...

Open a terminal, (Applications > Accessories > Terminal) and type

```
sudo apt-get update
```

Enter your password when prompted, you won't see it being entered but it will be.

Then try System > Administration > Hardware drivers again once the update is complete. You may see a driver for your wireless adapter in there.

---

### Post by bigups43 on 2010-03-16
I tried the command, and it did come up with two wireless drivers, but when I tried to activate them, it said SystemError: installArchives() failed.

It did find some drivers which is encouraging. Any ideas on the error message though?

---

### Post by Muzer on 2010-03-16
Give the output of the following command:

lspci -nn


If any of the devices have "Broadcom" in the name, try typing:

sudo aptitude install b43-fwcutter

Answer yes to any prompts you get, then reboot.


(Description of the commands - the first one LiSts all PCI devices inserted (which is how wifi cards are almost always connected internally), with the device Numbers as well as their full Names. The second one installs the b43-fwcutter package, which then proceeds to download and install firmware for the Broadcom wireless devices. This firmware is downloaded to the card on boot, and is required in order for it to work.)

---

### Post by bigups43 on 2010-03-16
You are a legend Muzer! It worked perfectly, soooo obliged!

---

### Post by devildoc5 on 2010-03-16
just in case you are still tweaking your hp I figured I would share this little jewwel with you.

[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html)

That has just about everything that either a dv9, dv6, ir dv2 has in it and how to get EVERYTHING working, whether natively or with workarounds...has been invaluable to me, as I have to dv9 Media.

OH yeah Welcome to Ubuntu!

---

### Post by bigups43 on 2010-03-17
thanks devil!

---

### Post by devildoc5 on 2010-03-17
Glad I could help...I know it helped me out a bunch...

---

### Post by dlucas86 on 2012-08-02
Unfortunately, I am not having the same luck getting my wireless card to work on my hp dv9000 laptop with a freshly loaded Ubuntu 12.04 image.  I got the Broadcom wireless card to show up in in the Additional Drivers window and it is green and activated and currently in use, but it is not showing up in the Networks window.  I tried installing b43-fwcutter and rebooting, but that still did not help.  Does anyone have any other ideas?  I'd really like to use Ubuntu with this laptop.

---

