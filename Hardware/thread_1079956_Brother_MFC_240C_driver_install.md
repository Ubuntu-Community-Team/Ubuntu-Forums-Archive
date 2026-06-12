---
title: "Brother MFC 240C driver install?"
date: 2009-02-24
forum: Hardware
---

### Post by lbetts on 2009-02-24
Thanks in advance.

I downloaded the drivers. (they are on the desktop)

I read the install instructions and got this message.

> betts@betts-desktop:~$ sudo dpkg -i --force-architecture mfc240clpr-1.0.0-9.i386.deb
dpkg: error processing mfc240clpr-1.0.0-9.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc240clpr-1.0.0-9.i386.deb
betts@betts-desktop:~$ 


I'm running an Acer Aspire with an AMD64 processor.
I downloaded the Ubuntu 64 bit version in the latest version.

What am I doing wrong?

---

### Post by TopEnder on 2009-02-24
G'Day,
Do a Search in Synaptic Package manage for your MFC-240C & hopefully you will fined something like : brother-cups-wrapper-bh7  & brother-lpr-drivers-bh7 if they are there install them and hopefully the printer side of the MFC-240C will work, if so come back to the forum and do a search for setting up the Scanner or ask for help the scanner is a little harder to install but many have got it to work.  TopEnder

---

### Post by OneIdle on 2009-08-25
Thank you for this!

---

### Post by aonegodman on 2009-08-26
Wow thanks for this post as it done the trick for me.

---

### Post by tal32123 on 2010-07-29
> **TopEnder said:**
> G'Day,
Do a Search in Synaptic Package manage for your MFC-240C & hopefully you will fined something like : brother-cups-wrapper-bh7  & brother-lpr-drivers-bh7 if they are there install them and hopefully the printer side of the MFC-240C will work, if so come back to the forum and do a search for setting up the Scanner or ask for help the scanner is a little harder to install but many have got it to work.  TopEnder

works like a charm :)

---

