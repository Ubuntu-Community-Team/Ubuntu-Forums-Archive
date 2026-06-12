---
title: "changing graphics cards"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by dphipps on 2005-06-27
I have been using a ATI Radeon 9000 but the fan on it has started to make a lot of noies so I switched to my onbord SiS graphics.  Now X11 will not start and all I get is a command line interface.  It works on the live CD so the SiS graphics must be suported.  What do I need to do reconfigure my conputer?

---

### Post by Unrivaled on 2005-06-27
I'm not sure what the SiS video driver's name is, but try this:

$ sudo vi /etc/X11/xorg.conf

Scroll down till you see:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"

or something like that.

You want to change the "fglrx" (or maybe it's "ati") to "sis"

If you don't know how to use vi, press "i" to go into insert mode, and "esc" to get out of insert mode. When you're done editing, exit insert mode and type ":wq" and hit enter. You should be back at the command prompt.
Try startx.

Hope this helps

---

### Post by frodon on 2005-06-29
to reconfigure xserver : 
```
sudo dpkg-reconfigure xserver-xorg
```

---

