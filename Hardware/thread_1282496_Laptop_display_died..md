---
title: "Laptop display died."
date: 2009-10-04
forum: Hardware
---

### Post by jays112 on 2009-10-04
My laptop display died on me, I have an Asus G1S-X1 with Ubuntu 9.04 on it. What are my options? How can I get VGA out to work?

Thanks for your Help..... I will really appreciate if someone can help.

Thanks

Jay :(

---

### Post by ermeyers on 2009-10-04
rename the "/etc/X11/xorg.conf" to "xorg.conf.bak"

sudo dpkg-reconfigure **-phigh** xserver-xorg

---

### Post by jays112 on 2009-10-06
> **ermeyers said:**
> rename the "/etc/X11/xorg.conf" to "xorg.conf.bak"

sudo dpkg-reconfigure **-phigh** xserver-xorg
Thanks for reply, but I cant see anything as monitor is black screen, I know I was able to log in. I am not sure if Ubuntu will detect display if I plug in VGA monitor to my laptop, or do a VGA to S Video to my TV.

Thanks

Jay

---

### Post by Sylslay on 2009-10-06
after blind login, conet any TV, CRT or LCD, and 
type :

gnome-display-properties
:guitar:

---

