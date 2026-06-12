---
title: "Need help for ATI display driver in Precise(12.04)"
date: 2012-11-12
forum: Hardware
---

### Post by heml0ck on 2012-11-12
Hello there,

So I'm trying to make a very ancient laptop ([Fujitsu Siemens Amilo M1425]("http://www.ailis.de/~k/archives/6-Linux-on-Fujitsu-Siemens-M1425.html")) make it recognize its own video card but its turning up more complicated than I've expected.

It has an &#65279;ATI Mobility Radeon 9700 under the hood, and [the instructions here]("http://www.unixmen.com/howto-install-ati-display-driver-in-ubuntu/") seemed to fit my purposes. However, at a certain step I came across this error and have no idea how to move forward. Any help is appreciated, I'm quite the linux newbie :(

> 
sudo dpkg -i fglrx*.deb
(Reading database ... 191028 files and directories currently installed.)
Preparing to replace fglrx-amdcccle 2:8.831-0ubuntu1 (using fglrx-amdcccle_8.831-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-dev 2:8.831-0ubuntu1 (using fglrx-dev_8.831-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-dev ...
Preparing to replace fglrx 2:8.831-0ubuntu1 (using fglrx_8.831-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx ...
dpkg: dependency problems prevent configuration of fglrx:
 fglrx depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev



---

### Post by Bashing-om on 2012-11-12
heml0ck; Hi ! Welcome to the forum.

I see this:
> 
Unpacking replacement fglrx ...
dpkg: dependency problems prevent configuration of fglrx:
 fglrx depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx (--install):
Install "dkms":
```
 apt-get install dkms
```and try to install the driver again; but do not be surprised if a proprietary driver does not run on "older" hardware/newer kernel .
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by QIII on 2012-11-12
Support for that chipset has been moved to a legacy driver branch and the legacy driver that supports it will not work with X Server versions post 2008.

Short of downgrading X Server to a much older version, which will undoubtedly cause catastrophic breakage, you will not be able to use any method to get a proprietary ATI driver to work.

You will have to stick with the open source Radeon driver used by default when you installed Ubuntu.

---

### Post by heml0ck on 2012-11-13
Thank you both for replies. The "dkms" option didn't solve it so I'll try again with Ubuntu 8.04

---

