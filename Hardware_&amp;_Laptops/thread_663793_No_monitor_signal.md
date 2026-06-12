---
title: "No monitor signal"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by martinic on 2008-01-10
Hello. I have just installed Gutsy on a desktop PC with an ATI Rage 128 graphics card. It all loads up fine until it gets to the login screen, at which point the monitor stops receiving a signal. Is there any way to rectify this?

---

### Post by taurus on 2008-01-10
Maybe boot int recovery mode from GRUB menu and reconfigure the X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by martinic on 2008-01-10
That just returns a series of errors beginning
FATAL: Error inserting battery (...) No such device.

---

