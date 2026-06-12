---
title: "Epson EPL 6200L on 14.04 LTS broken"
date: 2014-10-06
forum: Hardware
---

### Post by klbogotz on 2014-10-06
Hi,
after updating from 12.04 to 14.04 (new install) I'm unable to get my EPL 6200L to print.
It worked with 12.04 configured as described in [http://ubuntuforums.org/showthread.php?t=901529](http://ubuntuforums.org/showthread.php?t=901529)
I did all steps as in this HowTo outlined but no success.
Any help out there? Thanks

---

### Post by Vladlenin5000 on 2014-10-06
Hi, welcome.

No wonder an how-to from 6 years ago doesn't work... I'd be surprised, really surprised, if it did.

Now,
Epson EPL6200L historically has been a problem in Linux due to the non-standard communication protocols this model uses - [http://www.openprinting.org/driver/epsonepl](http://www.openprinting.org/driver/epsonepl) -, it has no proprietary drivers = not supported by the manufacturer. In spite of this a community project has been reported as working. Other good news is you no longer need to compile from source.

1. Go to [http://sourceforge.net/projects/epsonepl/](http://sourceforge.net/projects/epsonepl/) and download the deb file (should work in Ubuntu and any other Debian based Linux OS)

**For 32-bit:**
2. Double-click the downloaded file *ghostscript_8.14-2_i386.deb*. It should open with Ubuntu Software Center (or your default package manager). Install.
**-or-**
2. *cd *into the folder where you downloaded the file and ```
sudo dpkg -i ghostscript_8.14-2_i386.deb
```


**For 64-bit:**
2. Add the 32-bit architecture - the package is for 32-bit - with two commands:
```
sudo dpkg --add-architecture i386
sudo apt-get update
```

3. Double-click the downloaded file *ghostscript_8.14-2_i386.deb*. It should open with Ubuntu Software Center (or your default package manager). Install.
**-or-**
3. *cd *into the folder where you downloaded the file and ```
sudo dpkg -i ghostscript_8.14-2_i386.deb
```

---

### Post by klbogotz on 2014-10-06
Hi,
downloaded
[http://sourceforge.net/projects/epsonepl/files/ghostscript%20patched/Debian%20packages/ghostscript_8.14-2_i386.deb](http://sourceforge.net/projects/epsonepl/files/ghostscript%20patched/Debian%20packages/ghostscript_8.14-2_i386.deb)
double clicked
opens in Ubuntu Software Center
gives error: a newer package is yet installed
By the way: this package is from February 21th 2005, the HowTo I had followed is from August 26th, 2008
Any idea what I can do?
Thanks for your help
Klaus

---

