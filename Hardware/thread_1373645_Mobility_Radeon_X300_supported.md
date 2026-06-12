---
title: "Mobility Radeon X300 supported ?"
date: 2010-01-06
forum: Hardware
---

### Post by nicolasbol on 2010-01-06
Hi everybody,

My samsung died and I bought a refurbished T43, installed Ubuntu and it is working like a charm except that it seems there is an issue with the ATI drivers.

I tried to go into System>Administration>Hardware Drivers to get better performance but the list is empty.

I tried to check ```
/etc/X11/xorg.conf
```: It's not there either.

Tried to rebuild xorg.conf with ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` but still no xorg.conf.

Tried to install ATI Catalyst Control Center but it won't start: Even ```
aticonfig
``` fails and return ```
aticonfig: No supported adapters detected
```I have no idea how to resolve this.

---

### Post by nicolasbol on 2010-01-06
Ok, looks like ATI dropped support for X300.

I'm going to downgrade my installation to Ubuntu 8. Let me know if there is a better solution :/ !

---

