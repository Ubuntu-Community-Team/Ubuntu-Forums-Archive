---
title: "Ok, now I can't choose a screen resolution higher than 800 x 600"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by Cornellius on 2005-06-19
What can I do ?

---

### Post by diebels on 2005-06-19
[QUOTE=Cornellius]What can I do ?[/QUOTE]
 ?

---

### Post by bored2k on 2005-06-19
[QUOTE=diebels]?[/QUOTE]
 **Do not **do this, specially after only 3 minutes.

sudo dpkg-reconfigure xserver-xorg && sudo restart

---

### Post by rider343 on 2005-06-19
post here your /etc/X11/xorg.conf

---

### Post by az on 2005-06-20
[QUOTE=bored2k]
sudo dpkg-reconfigure xserver-xorg && sudo restart[/QUOTE]

CRTL-ALT-F1 (to get our of X)

sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg
#Here, try chosing a lower color depth, if you have an older card (like try 15-bit instead of 24)


sudo /etc/init.d/gdm start



You do _not_ need to reboot.

---

