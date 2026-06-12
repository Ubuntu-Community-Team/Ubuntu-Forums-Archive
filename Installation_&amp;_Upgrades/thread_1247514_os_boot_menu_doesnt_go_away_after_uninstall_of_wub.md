---
title: "os boot menu doesnt go away after uninstall of wubi"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by rhythmiccycle on 2009-08-23
i had Ubuntu 9 installed inside windows xp dell laptop

after i uninstalled it from within windows, all the files are gone, but i still get the os boot menu at start up. 

How do i make that go away?

---

### Post by Partyboi2 on 2009-08-23
Hi, you need to manually remove the entry for Ubuntu wubi from your boot.ini file.
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by raymondh on 2009-08-23
or ... have a look-see at the [wubi-guide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?").  As partyboi referenced, you'll have to manually edit the boot.ini file and delete **_JUST_** the wubi-referenced lines.

Just the wubi/ubuntu lines .......

---

