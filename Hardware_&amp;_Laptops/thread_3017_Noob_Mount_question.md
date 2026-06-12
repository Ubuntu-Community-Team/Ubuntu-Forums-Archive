---
title: "Noob Mount question"
date: 2004-11-02
forum: Hardware &amp; Laptops
---

### Post by jdusablon on 2004-11-02
Noob question:

what kind of fstab or other settings does one need to set in order to have external (1394/USB2) devices mount and unmount by plugging them in like with (cringe) WinXP/2K?

If so, can these devices "appear" in Nautilus automatically? How?

---

### Post by jdong on 2004-11-02
Err, they should automatically do so already... That's the whole theory behind HAL and Project Utopia.


Can you post **dmesg** and **tail -n=30 /var/log/daemon.log** output?

---

