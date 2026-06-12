---
title: "Lenovo laptop consumes power when turned off"
date: 2014-08-29
forum: Hardware
---

### Post by mejrum on 2014-08-29
Hi
Running Lenovo T431s with SSD only disk, Ubuntu 14.04.
The power keeps draining when the power is completely turned off.

I've disabled Wake-On-LAN both in BIOS and with /etc/rc.local: /sbin/ethtool -s eth0 wol d
I've disabled USB 'power always on' feature in BIOS.

What else could it be? How can I diagnose further?

---

### Post by MartyBuntu on 2014-08-29
Is this a single-boot machine? Do you have any other OS installed?

---

### Post by mejrum on 2014-09-02
I'ts single-boot, only Ubuntu installed.

---

### Post by MartyBuntu on 2014-09-04
Read this:
[http://ubuntuforums.org/showthread.php?t=2052582](http://ubuntuforums.org/showthread.php?t=2052582)

---

