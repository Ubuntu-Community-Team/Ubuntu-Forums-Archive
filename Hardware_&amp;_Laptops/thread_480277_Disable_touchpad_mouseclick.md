---
title: "Disable touchpad mouseclick"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by frodex on 2007-06-21
Hi, I'm using a Fujitsu-Siemens E model laptop with mouse touchpad.  Problem is that the touchpad is way sensitive, registering the smallest tap as a click.  This is extremly annoying so I need a way to disable (or adjust sensitivity) tap=click but keep the pad functional for cursor movement.  Can this be done?

edit: The sensitivity was never a problem running WinXP earlier.

---

### Post by Ayuthia on 2007-06-21
You might check this out:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Disable_the_touchpad_while_typing](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Disable_the_touchpad_while_typing)

I am not for sure if you have a synaptics touchpad or not, but this helped my HP Pavillion dv6338se.

---

### Post by frodex on 2007-06-22
Thanks for your help!

This turned out to be the soltuion for me:

> 
In Gnome:
sudo apt-get install gsynaptics
And go to System > Preferences > Touchpad <- there you can disable tap-click


---

### Post by schucki.be on 2007-06-26
Worked for me !
Do not forget to set SHMconfig to true /etc/X11/xorg.conf, in the Synaptics section.

Thnx,
Schucki.be

---

### Post by mikeypizano on 2007-06-26
Thanks, I have been looking for something like this.

---

### Post by mastergunner on 2007-08-26
......

---

