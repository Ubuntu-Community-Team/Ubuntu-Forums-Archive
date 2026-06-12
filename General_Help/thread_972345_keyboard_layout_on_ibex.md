---
title: "keyboard layout on ibex"
date: 2008-11-05
forum: General Help
---

### Post by galia on 2008-11-05
I have re-installed ibex on top of the hardy (instead of upgrading- big mistake). Anyway, I lost my customised keyboard layout which I have planted in the "/etc/x11/xkb/symbols" folder on the hardy os. This folder does not exit any more. I tried to plant that file in "/usr/share/x11/xkb/symbols" but the layout option does not appear in the gnome list of languages (like it did with the hardy).
Also there is a note in the "/etc/x11/xorg" file that the system does not read it any more and therefore changes made to it will not apply. The section I used to toggle between languages which looked like this:

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"   "pa,il"
    Option        "XkbOptions"  "grp:shift_caps_toggle"
EndSection

(pa- being the new layout file I've planted in the "/etc/x11/xkb/symbols")

also doesn't exit in the xorg file.
Actually there is no "section InputDevice" for keyboard at all.

Any idea on how to manipulate the keyboard layout on ibex?
thank you for your help,
Galia

---

### Post by kellner on 2008-11-09
From another thread, I learned that reconfiguring the keyboard is done in Ibex with sudo dpkg-reconfigure console-setup. 

However, it seems that this program does not read the symbol tables from /usr/share/X11/xkb/symbols - at least not on my installation. 

Try this: change the description of a keyboard variety in one of the symbol files (e.g. "German - dead grave acute" to "German - absolutely dead"). Then call dpkg-reconfigure and see whether that change is reflected in the list - on my installation, it isn't. 

But from where does dpkg-reconfigure take this information? I did a recursive grep on all files in /etc and /usr for the keyboard description strings, but couldn't find them. It's a mystery to me ...

b

---

### Post by bmroute on 2008-11-29
I had this exact same problem when I upgraded to Ibex, and after some playing around with some XML files I think I've found the file that most likely caused my layout to be excluded from the list.

Make a new <variant> (or <layout>, whichever is appropriate) entry in **/usr/share/X11/xkb/rules/evdev.xml** for your layout, and it should probably show up in the list. If not, put it in all of the other XML files (base.xml, xorg.xml, etc). I put my layout in every XML file and it didn't show up in the list until I put it in evdev.xml, so I'm assuming that's the file that it's reading from. There is no need to do sudo dpkg-reconfigure console-setup, I just updated the file, logged out and back in, and it was there. Hope this helps.

---

