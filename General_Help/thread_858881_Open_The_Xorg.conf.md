---
title: "Open The Xorg.conf"
date: 2008-07-14
forum: General Help
---

### Post by Uchiha_madara on 2008-07-14
Good Morning 

,

I forget the way to reach Xorg.conf By Using terminal 


1 --can you make me remember ??

2 -- if there is a network, and the Administrator Hides a details from you

can I access these details from terminal (y/n)??

---

### Post by jolx on 2008-07-14
sudo vim /etc/X11/xorg.conf

dunno about 2

---

### Post by aysiu on 2008-07-14
vim's good if you know how to use it, but it confuses the hell out of me. If you're a novice text editor user like me, you can try ```
sudo nano -B /etc/X11/xorg.conf
``` or ```
gksudo gedit /etc/X11/xorg.conf
```

---

