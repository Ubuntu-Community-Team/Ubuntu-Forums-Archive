---
title: "Simple Radeon 9600 Question - Stuck"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by uberamd on 2007-04-26
I downloaded the driver for my Radeon 9600 from ATI.com, and I am running Ubuntu 7.04.

I try to install the driver by doing:
```
sudo -s 'ati-driver-installer-8.36.5-x86.x86_64.run'
```
The terminal has the following output:
```
Created directory fglrx-install.Ua5677
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.36.5...............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.2.x

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        X.Org 7.1.x
    x710_64a    X.Org 7.1.x 64-bit
Removing temporary directory: fglrx-install.Ua5677
```

So basically it tells me to override the X-Version with my version. So first, what is the X_VERSION for Ubuntu 7.04, second how would I use that flag to get the driver to install. I have tried variations of ```
sudo -s 'X_VERSION=x710 ati-driver-installer-8.36.5-x86.x86_64.run'
``` and what not but it tells me it is invalid syntax.

Any ideas?

Thanks.

---

### Post by jalefkowit on 2007-04-26
I got the same error when I tried to install fglrx on my Feisty box, too (which also has a Radeon 9600). I never did figure out what it means, but it turns out that if you just use [Envy]("http://albertomilone.com/nvidia_scripts1.html") to install the driver it handles the problem automatically. So my recommendation would be to try Envy before you pull any hair out deciphering the error :-)

---

### Post by uberamd on 2007-04-26
Worked like a charm, thanks a lot!

---

### Post by superyounan1 on 2007-05-01
hey guys, im looking to do the same, I have XGL running for desktop effects nicely, but i want the catalyst control center.

Do you guys have XGL, and have you had any problems with it since the update to the newest driver?

---

### Post by THAiSi on 2007-05-01
You get the control center using envy.

to start the control center, type at the console:
amdcccle

---

### Post by superyounan1 on 2007-05-04
I have envy, but I'm reluctant to update because there are dozens of threads of people complaining of so many problems after upgrading to 8.35.6

---

