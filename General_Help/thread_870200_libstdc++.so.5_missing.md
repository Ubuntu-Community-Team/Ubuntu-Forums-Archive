---
title: "libstdc++.so.5 missing"
date: 2008-07-25
forum: General Help
---

### Post by TXMUSICTRUCKER on 2008-07-25
Ubuntu 8.04 KDE desktop trying to install Lexmark Z611 drivers. Drivers show installed. When:   /usr/lib/cups/backend/z600 is inputed in terminal then: missing libstdc++.so.5 is the output in terminal. I refer to: 

[http://ubuntuforums.org/showthread.php?t=842493](http://ubuntuforums.org/showthread.php?t=842493)

libstdc++.so.5 is not available in apt-get or Package manager.

I have successully installed these drivers in Mepis a year back using these or similar instructions. Though using distros for a year or so I am a newbie to Linux as far as really knowing how to be an administrator. Any help is greatly appreciated. Thanks! 

TXMUSICTRUCKER

---

### Post by ryanhaigh on 2008-07-28
Using the [ubuntu package search]("http://packages.ubuntu.com/search?searchon=contents&keywords=libstdc%2B%2B.so.5&mode=exactfilename&suite=hardy&arch=any") to locate packages containing that file indicates that you need [apt://libstdc++5]("apt://libstdc++5")

---

### Post by ceclauson on 2008-07-28
If that doesn't work, I found a similar problem with a google search:
[http://marc.info/?l=xerces-c-users&m=112845633501219&w=2](http://marc.info/?l=xerces-c-users&m=112845633501219&w=2)

---

### Post by gansvv on 2010-07-10
Use the download link from 
[http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download) and install.

E.g.:
```

wget http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb

sudo dpkg -i libstdc++5_3.3.6-18_i386.deb 

```

For 62bit: [http://packages.debian.org/stable/base/libstdc++5](http://packages.debian.org/stable/base/libstdc++5)

---

### Post by flint_ on 2010-07-29
Greetings,

It turns out that the June 2009 version of the IBM z/VSE Softcopy Reader cannot operate without libstdc++.so.5.  The error in the log file (~/.IBM/SCR/hlcb.log)looks like this:

Exception in thread "main" java.lang.UnsatisfiedLinkError: /opt/scr/sys/libhlcwam.so: libstdc++.so.5: cannot open shared object file: No such file or directory

Your answer, to acquire and install: 
wget [http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb](http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb)
sudo dpkg -i libstdc++5_3.3.6-18_i386.deb

Did the trick.  Thanks!!!

Wednesday, July 06 2011
You will find scripts that work to start the IBM softcopy reader and bookshelf system at the site below:
[http://docbox.flint.com/~flint/ibm-softcopy-bookreader/](http://docbox.flint.com/~flint/ibm-softcopy-bookreader/)

---

