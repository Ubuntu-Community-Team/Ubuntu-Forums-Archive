---
title: "How to permanently set keyboard layout with xorg.conf"
date: 2008-08-19
forum: General Help
---

### Post by eragon100 on 2008-08-19
Hi guys!

How do I permanently select us international with dead keys as a layout in xorg.conf, (so ´ + e creates an accented e), because the setting isn´t remembered when I set it in keyboard preferences? I have already tried to do it myself, so this is my current xorg.conf keyboard section:

Now what is the name for the layout us international with dead keys, instead of just us international?

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbVariant" "intl"
EndSection

---

### Post by ellgor on 2008-08-19
Hi,

Have you tried this way, open a terminal and type in:

sudo dpkg-reconfigure xserver-xorg

A small window will be presented and if everything else is fine accept the settings (arrow keys and enter) when presented, until you come to the keyboard section, make sure the lang is set to " us " and whilst there, there are settings for making dead keys etc adjust accordingly, hope this helps.

Regards, Ellgor.

---

### Post by eragon100 on 2008-08-19
Thanx, but wouldn´t disable the nvidia binary driver?

---

