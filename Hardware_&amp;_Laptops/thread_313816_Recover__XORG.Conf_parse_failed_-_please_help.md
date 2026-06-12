---
title: "Recover / XORG.Conf parse failed - please help"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by b3n87 on 2006-12-06
Hello, i was following a Beryl wiki page i found on the ubuntu website and i restart the X server, and now ubuntu wont boot.

It is coming up with the following errors

An error about multi Indentifier's in Screen section

and fatal error, no screen found


I no how to fix the error, its because i changed /etc/X11/xorg.conf incorrectly, i just need help on how to open the file to edit it, or recover the system some how.

Thanks in advance


Ubuntu Edgy 6.10

Ben

---

### Post by taurus on 2006-12-06
Boot into recovery mode from GRUB menu and at the prompt, type

```
nano -w /etc/X11/xorg.conf
startx
```

---

### Post by b3n87 on 2006-12-06
thanks for you quick reply

i was just about to post saying if you run this command

sudo dpkg-reconfigure xserver-xorg

then

startx


your sorted :)

thanks again

---

