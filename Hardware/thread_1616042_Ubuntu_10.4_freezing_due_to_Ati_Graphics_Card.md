---
title: "Ubuntu 10.4 freezing due to Ati Graphics Card"
date: 2010-11-07
forum: Hardware
---

### Post by JeffGraham on 2010-11-07
Hey. Complete Linux Newbie here. I installed 10.4 on my desktop about 2 weeks ago and it freezes almost immediately after startup. When I run Linux in low graphics mode it works fine except that internet video doesn't work well. I have an ati x1300 graphics card, I'm running the open source driver. I can't figure out how to install fglrx, or switch the open source drivers, or install the most updated driver. I guess I'm used to Windows doing everything for me. Any help is appreciated!

-Jeff-

---

### Post by Yellow Pasque on 2010-11-07
ATI doesn't support your card anymore . Don't even try to install fglrx unless you want to screw up your system.

---

### Post by JeffGraham on 2010-11-08
That's what I keep reading (about fglrx). I downloaded [this ]("http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html")driver, but can't figure out how to install it.

---

### Post by mastablasta on 2010-11-08
this driver is not for your card. your card is no longer supported by ATI.
 
do not try to install fglrx (or any of proprietary) drivers because you will mess up the system. they do not support current Ubuntu.
 
you need to use open source drivers. maybe what you could do is try to update the opensource ones to testing (beta) version.

---

### Post by JeffGraham on 2010-11-08
@mastablasta- sorry for being dumb, but how do I go about using the beta driver? I did find and download the driver for 10.10, but now I don't know how to install/use it. When I double click the file it asks what program I'd like to use, and I don't know which one to use.

---

### Post by Yellow Pasque on 2010-11-08
LMAO. Stop trying to install that (fglrx). Here: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

