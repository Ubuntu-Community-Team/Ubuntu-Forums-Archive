---
title: "Monitor Configuration"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by arunsub on 2005-06-01
Is there any way I can change my monitor through GUI without reinstalling/reconfiguring xserver? i.e. Any option in GNOME that I can use to configure the monitor from generic to Dell?

---

### Post by Mez on 2005-06-01
your best bet is to open a console and type

```
sudo dpkg-reconfigure xserver-xorg
```

Then when you have done this - hit ctrl+alt+backspace to restart X

---

