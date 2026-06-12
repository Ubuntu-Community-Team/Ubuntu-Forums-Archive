---
title: "How to change a display resolution"
date: 2008-07-03
forum: Hardware
---

### Post by charleshdw on 2008-07-03
I have Toshiba Dynabook, now a display resolution is 640x..(I don't remember yet).
and i want to change it to 800x600.
Please give me solusion.

---

### Post by erginemr on 2008-07-03
Please take a back up of your current X config file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```

and try the following from the terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

