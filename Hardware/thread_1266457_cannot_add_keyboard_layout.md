---
title: "cannot add keyboard layout"
date: 2009-09-14
forum: Hardware
---

### Post by wormhole on 2009-09-14
First of, are locales necessary in order to use keyboard layouts ?
In order to save space, I've removed all locales but the en_*.
After an upgrade to Kubuntu 9.04, the Romanian layout didn't show in the layout switcher, but Swedish, Norwegian, Icelandic and German did (and work just fine).. though another strange thing happened. I removed the Norwegian layout and was no longer able to add it back (the add button is active but does nothing). Actually I cannot add any other layout.
I've added RO locale but to no avail. And I cannot change the layout list with setxkbmap (strangely, "**setxkbmap no**" works, though no doesn't appear on the layout list),
I wanted to edit xorg.conf, but the keyboard section is commented by aptitude and it mentions HAL as the prefered way.

output of 
**setxkbmap -print** :
xkb_keymap {                       
        xkb_keycodes  { include "evdev+aliases(qwerty)" };
        xkb_types     { include "complete"      };        
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc+us+se:2+de:3+is:4+inet(evdev)+group(alt_shift_toggle)"      };
        xkb_geometry  { include "pc(pc105)"     };
};

**setxkbmap -model pc105 -layout us,se,de,no,is,ro -v 10**
Setting verbose level to 10
locale is C
Warning! Multiple definitions of keyboard model
         Using command line, ignoring X server
Warning! Multiple definitions of keyboard layout
         Using command line, ignoring X server
Applied rules from evdev:
model:      pc105
layout:     us,se,de,no,is,ro
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc+us+se:2+de:3+no:4+inet(evdev)
geometry:   pc(pc105)


I'm using Kubuntu 9.04 (KDE 4.3.1, though I don't think it's a KDE issue).

---

### Post by wormhole on 2009-10-03
The problem is a bug in[SIZE=1]** /usr/bin/kxkb**: [http://www.mail-archive.com/debian-qt-kde@lists.debian.org/msg25253.html](http://www.mail-archive.com/debian-qt-kde@lists.debian.org/msg25253.html) that doesn't allow more than 4 layouts to be set. 
[/SIZE]

---

