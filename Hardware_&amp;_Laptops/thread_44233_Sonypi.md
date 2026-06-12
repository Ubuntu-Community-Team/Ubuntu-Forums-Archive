---
title: "Sonypi"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by rathel on 2005-06-25
I have ubuntu running on a sony vaio laptop and i've got a problem. I'm trying to increase my brightness and I get this error:
```

rathel@ubuntu:/etc/init.d$ sudo spicctrl -b 255
Password:
/dev/sonypi: No such file or directory

```
How do I create that file or directory?

---

### Post by rathel on 2005-06-25
okay now I created that file/folder now i'm running into another problem!
```

rathel@ubuntu:~$ sudo spicctrl -b 255
ioctl: Invalid argument

```

---

### Post by rathel on 2005-06-26
Okay, Now I removed Ubuntu and reinstlaled windows and used that utility to brighten the screen, now all is good, but I tried to use spicctrl again and this time No Error messages... and nothing changes.

---

