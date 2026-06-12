---
title: "nano /etc/x11/xorg.conf.....help"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by gordong11 on 2006-02-11
Hello,

When I go into this file, There is nothing there just a navagation menu at the bottom. I'm having video problems and want to change "ATI" to VESA", but I dont get anything the menu to change. just blank. Any ideas?

---

### Post by heimo on 2006-02-11
Did you enter the path correctly, it's case sensitive and it should have **X**11, not x11.
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by aysiu on 2006-02-11
I'm with Heimo on this one.

Of course, if you absolutely can't find it, you can always do Control-Alt-F1, log in, and then ```
sudo dpkg-reconfigure xserver-xorg
```

---

