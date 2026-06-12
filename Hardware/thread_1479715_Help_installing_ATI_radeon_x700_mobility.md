---
title: "Help installing ATI radeon x700 mobility"
date: 2010-05-10
forum: Hardware
---

### Post by fenririx on 2010-05-10
Trying to restore my gaming laptop to former glory.
I tried installing the proprietary drivers for an ATI radeon x700 mobility on ubuntu 9,but it crashed to system. i now have ubuntu 10 and need help installing the drivers. Any information would be great i know ati put the driver out i just cant get it to install

---

### Post by parn on 2010-05-11
The last I check, ATI X700 is not supported by ATI Catalyst Proprietary drivers. You have to use the Open Source driver.

---

### Post by khelben1979 on 2010-05-11
If you decide on using Ubuntu, you haveto use an older version of Ubuntu because prop. drivers are not compatible with newer versions of the x server which is provided by Ubuntu Lucid or Karmic.

Go for the open source video driver if you don't want to use an old version of Ubuntu. It's provided by the Linux kernel and can be used by altering your /etc/X11/xorg.conf file where the graphics configuration file is.

---

