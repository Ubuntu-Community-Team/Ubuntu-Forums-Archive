---
title: "Keyboard X Error"
date: 2005-11-24
forum: General Help
---

### Post by smgil on 2005-11-24
Hi.

I've just upgrade to Breezy from Hoary and I can't login. 


It seems like key board isn't working, when I try to put my username and password nothing appear on screen.I can change to terminal (Ctrl-Alt-1) and login in normal way but in GDM keyboard only response to function keys, caps lock and arrows, no letters work. 


Any idea ?

---

### Post by Xian on 2005-11-24
Look at your xorg.conf file & see what settings are used for your keyboard. ```
$ sudo nano -w /etc/X11/xorg.conf
```

Or you could reconfigure X from scratch. 

```
$ sudo dpkg-reconfigure xserver-xorg
```

---

