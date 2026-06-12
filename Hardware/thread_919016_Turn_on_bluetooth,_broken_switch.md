---
title: "Turn on bluetooth, broken switch"
date: 2008-09-13
forum: Hardware
---

### Post by lian1238 on 2008-09-13
Hi guys,
On my acer aspire laptop, the bluetooth toggle switch has broken. Is there a way to turn it on with a command? In windows, the acer power management can do it. How to do it in Ubuntu?

---

### Post by lian1238 on 2009-08-12
Wow, I found a way! (unintentionally!)

Edit the file /sys/bus/platform/devices/acer-wmi/bluetooth
Just put a **1** into the file to turn **ON**, or **0** to turn **OFF**, the bluetooth!

For example, to turn ON bluetooth:
```
cd /sys/bus/platform/devices/acer-wmi/
sudo echo "1" > bluetooth

```

To turn off, just change "1" to "0".

---

