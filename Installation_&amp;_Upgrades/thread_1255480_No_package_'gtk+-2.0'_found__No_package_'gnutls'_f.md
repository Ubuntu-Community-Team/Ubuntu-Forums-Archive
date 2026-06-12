---
title: "No package 'gtk+-2.0' found  No package 'gnutls' found No package 'pygtk-2.0' found"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by ionoff on 2009-09-01
This post is in reply to an archived post at [http://ubuntuforums.org/showthread.php?t=304763](http://ubuntuforums.org/showthread.php?t=304763)

It is meant to solve some people's problems when searching.

When I state XXXXX fixed it, do an sudo apt-get install XXXXX where XXXXX is the package name to fix the issue yourself.


When I was configuring OpenXenCenter, I was getting a few depends, one was this GTK+ one

```

checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.10.0) were not met:

No package 'gtk+-2.0' found

```
**libgtk2.0-dev** fixed it



Some additional depends it needed:

then had
```

checking for GNUTLS... configure: error: Package requirements (gnutls >= 1.4.0) were not met:

No package 'gnutls' found

```

libgnutls-dev fixed it


then had
```

checking sasl/sasl.h usability... no
checking sasl/sasl.h presence... no
checking for sasl/sasl.h... no
checking for sasl_client_init in -lsasl2... no
configure: error: You must install the Cyrus SASL development package in order to compile GTK-VNC

```
libsasl2-dev fixed it

then had
```

checking for PYGTK... configure: error: Package requirements (pygtk-2.0 >= 2.0.0) were not met:

No package 'pygtk-2.0' found

```

python-gtk2-dev fixed it



Hope this helps

---

### Post by vforge37 on 2010-06-11
It helped immensely, THANK YOU!!!:p

---

### Post by User Abuser on 2010-07-15
Thanks a bunch. If I knew source needs 100megs dl I would never try it :D

---

