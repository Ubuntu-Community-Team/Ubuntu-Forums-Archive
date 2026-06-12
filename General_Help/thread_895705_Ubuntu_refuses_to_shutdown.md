---
title: "Ubuntu refuses to shutdown"
date: 2008-08-20
forum: General Help
---

### Post by crazydavythe1st on 2008-08-20
When I attempt to shutdown through the GUI, the screen goes black, and then the login screen reappears. When I try

sudo shutdown now

The computer starts to shutdown and then shows a recovery screen with these options:

boot   resume normal boot
dpkg   fix broken packages
xfix   fix X window system

and then one more option that has to do with booting to a basic terminal or something like that. Regardless I end up at the login screen again. I haven't seen anyone else address this, so I'm kind of clueless...

---

### Post by Potatoj316 on 2008-08-20
try
```
sudo shutdown now -P
```
or maybe
```
sudo shutdown now -H
```

---

### Post by mickey13 on 2008-08-20
I use:

sudo poweroff

OR

sudo reboot

---

### Post by khelben1979 on 2008-08-20
If I can't reboot a Linux system through it's GUI I always do: shutdown -h now. Always works for me, although I have no experience by using Ubuntu myself (I'm not a fan of Ubuntu..)

---

### Post by LateNiteTV on 2008-08-20
on my freebsd, 
```
halt -p
```
does it for me.

---

