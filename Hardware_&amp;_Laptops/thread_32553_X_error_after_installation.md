---
title: "X error after installation"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by Jedidawn on 2005-05-08
I have just installed Ubuntu. After the installation, Ubuntu  gave an error saying it could not start x and asking if I wanted to see x's diagnostic report I answered yes but couldn't understand it. I pressed enter and it booted me to the command line. I tried to start x from there and it gave me this error: ```
XI0: fatal error 104 (connection reset by peer) on x server ":0.0"
after 0 requests (0 known processed) with 0 events remaining
```

---

### Post by Jedidawn on 2005-05-08
Oh I just remembered; the live cd worked correctly

---

### Post by Jedidawn on 2005-05-09
anybody?

---

### Post by daniels on 2005-05-09
If you could find a way to attach /var/log/Xorg.0.log, that would help enormously.

---

### Post by Jedidawn on 2005-05-10
Here (used explore2fs)

---

### Post by Jedidawn on 2005-05-11
Hello?

---

### Post by poofyhairguy on 2005-05-12
[QUOTE=Jedidawn]Hello?[/QUOTE]

Hello. Sorry it took a while, there are lot of people that want help here and not as many helpers now a days.

Do me a favor. Send me a private message with the contents of your xorg file. To get it , type:

sudo gedit /etc/X11/xorg.conf

I'll look at it and see whats wrong...

---

