---
title: "* Starting Avahi mDNS/DNS-SD Daemon avahi-daemon   [fail]"
date: 2009-03-16
forum: Hardware
---

### Post by araz_aslan on 2009-03-16
Hi every on 
i  get in trouble recently,when it is booting shows an error like this 
 ```
* Starting Avahi mDNS/DNS-SD Daemon avahi-daemon   [fail] 
```
i tried to reinstall avahi and HAL, but it is not fixed and new problem occurred and now when i log in to my desktop, it just shows a blank screen( i have been issued apt-get remove --puge hal command before).
how ca n fix this problem.
again i have been tried to issue and download and compile packages like hal, avahi and  dbus but none of them solved the problem.
My  Laptop [BenQ jooybook 7000 ]("http://benq.com/products/joybook/?product=582") and My OS is Ubuntu Hardy Heron
Regards
Araz aslan

---

### Post by nelskurian on 2009-03-16
Avahi-daemon somes times causess problems.So just disable avahi-daemon by

```
gksu gedit /etc/defaults/avahi-daemon
```

AVAHI_DAEMON_DETECT_LOCAL=0

Enter it for deactivating it while booting.

---

