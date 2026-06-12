---
title: "Incorrect Keyboard Layout"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by iamadam on 2007-07-18
Hi,

I'm fairly new to Linux so go easy on me :) I'm having trouble with my keyboard layout in Xubuntu 7.04. The keyboard section of my xorg.conf is:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

The 'XkbLayout' is correct but it seems to be using a US layout for some reason. I added the 'Keyboard Layout Switcher' item to my desktop panel and the US flag comes up. Any ideas?

UPDATE: Giving up on Xubuntu. Ubuntu seems to be a much more polished distro.

---

### Post by hangthedj on 2007-07-20
Have you tried running dpkg-reconfigure xserver-xorg, and changing the options in there it asks for?

---

