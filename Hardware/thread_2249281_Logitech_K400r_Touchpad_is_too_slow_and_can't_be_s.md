---
title: "Logitech K400r Touchpad is too slow and can't be sped up via System Settings"
date: 2014-10-20
forum: Hardware
---

### Post by sjeon on 2014-10-20
**OS & Hardware**
Ubuntu 14.04 LTS 64bit
Logitech K400r USB Wireless Keyboard+Touchpad

**The problem**
The touchpad is moving too slow. It doesn't show up in System Settings.

**My temporary solution (A bash script)**
mouseid=$(xinput | grep "Logitech Unifying" | grep -oP id=[0-9]+ | awk -F= '{print $2}')
echo mouseid = $mouseid
xinput --set-prop $mouseid 266 0.4

**Thoughts**
+ This device's mousepad oughta be visible and adaptable in cursor speed via System Settings. Currently does not appear to be.

---

