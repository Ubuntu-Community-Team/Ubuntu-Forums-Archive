---
title: "how change the ALT key to other key"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by frankabel on 2007-02-26
Hi,

My laptop have the ALT key broken. How can I change the ALT key to other key. What I need is that when I press the other key linux think that the ALT key was pressed.

Salute
Frank Abel

---

### Post by frankabel on 2007-12-09
Auto reply ;) 

with xev get the keycode of the key that will work as Alt and then

xmodmap -e 'keycode 115 = Super_L'

but change 115 with the keycode of the key you want

Help me this post [http://ramblings.narrabilis.com/wp/binding-windows-key-to-gnome-foothat-panel-menu/](http://ramblings.narrabilis.com/wp/binding-windows-key-to-gnome-foothat-panel-menu/)

---

