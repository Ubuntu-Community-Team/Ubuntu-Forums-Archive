---
title: "I need help setting my console resolution."
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by atomicthumbs on 2007-09-30
My story:

Laptop: Dell Inspiron 8200
Screen size: 1400x1050
My console size: Tiny
My distro: Kubuntu Feisty

:confused:

I've tried various framebuffer things in menu.lst, but they always either tell me that I have an invalid mode number or they don't do anything. Could somebody help me do this using mesa or vesafb or something? Thank you!

---

### Post by kellemes on 2007-09-30
I have a 1680x1050 monitor and use vga=775 without issues..
Did you try this already?
Here more options..

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+

---

### Post by atomicthumbs on 2007-09-30
None of those are 1400x1050, sadly. I tried the one in the menu.lst comments (vga=791), and it works. Unfortunatly, it's 1024x768 (I think), and the font is weird. Somebody has to have this working. I need your mode number, please!

If this helps:

video card: nVidia Geforce 2 Go (32MB RAM, nvidia driver for X)

---

### Post by atomicthumbs on 2007-10-01
Hello?

---

