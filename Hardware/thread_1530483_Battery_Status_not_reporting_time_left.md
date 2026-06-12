---
title: "Battery Status not reporting time left"
date: 2010-07-13
forum: Hardware
---

### Post by Pyronhell on 2010-07-13
Hi!

I'm using Ubuntu 10.04 64bits on a Toshiba Satellite A500-18Q and the Battery Status applet is not reporting me the time left when I'm using the laptop with the battery.

Also:
```
pyronhell@pyronhell-laptop:~$ acpi
Battery 0: Discharging, 97%, discharging at zero rate - will never fully discharge.
```

I'm using the Battery Status applet, but was the same thing with the one that comes with ubuntu.

Anyone have any idea that why this happens?

Thanks in advance.

---

### Post by mörgæs on 2010-07-14
The battery indicator showing strange values is a known bug. 

There is a report here
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/120258](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/120258)
(and others in Launchpad)

---

