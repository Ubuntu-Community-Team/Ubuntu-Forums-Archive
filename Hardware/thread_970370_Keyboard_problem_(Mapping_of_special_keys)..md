---
title: "Keyboard problem (Mapping of special keys)."
date: 2008-11-04
forum: Hardware
---

### Post by IzuliuM on 2008-11-04
Hi,

I got several problems with upgrade from 8.04 to 8.10 but I didn´t get one problem from 7.10 to 8.04.

My hardware is: ¨Dell Latitude D830¨

My ubuntu is up to date (aptitude update + aptitude upgrade). I´ve searched on google and ubuntu forums without success.

My keyboard doesn´t work properly. Mapping seems incorrect especially for special keys. I´ve edited xorg.conf to change conf without success:

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

I´ve also changed conf using System > Preferences > Keyboard under Gnome without success.

Keyboard Preferences:
- Dell Latitude series laptop,
- USA Alt (us_intl).

I can check keys when I´m in ¨Choose a Layout¨ (USA/us_intl):
- ¨Page Up¨ seems not mapped,
- ¨Page Down¨ seems mapped on ¨Menu¨,
- ¨Down¨ seems not mapped,
- ¨Up¨ seems mapped on ¨Print Screen¨,
- ¨Print Screen¨ seems mapped ¨Delete¨,
- ¨Delete" seems not mapped,
- ...

Sound keys don´t work but it is not critical.

The problem is also there with standard USA keyboard (us).

Let me know if you need more information...

Tks for your help !

---

### Post by IzuliuM on 2008-11-05
Hi,

I´ve also tried to update xkb-data package as mentioned in another thread but the version was correct. I´ve reinstalled package without success.

Command line used:
sudo aptitude reinstall xkb-data

Link:
[http://ubuntuforums.org/showthread.php?t=915183&highlight=keyboard+problem+special](http://ubuntuforums.org/showthread.php?t=915183&highlight=keyboard+problem+special)

Package version (on [http://packages.ubuntu.com/):](http://packages.ubuntu.com/):)
intrepid (x11): X Keyboard Extension (XKB) configuration data
1.3-2ubuntu4: all 

Package version (on my laptop with ¨sudo dpkg -l | grep xkb¨):
ii  xkb-data   1.3-2ubuntu4   X Keyboard Extension (XKB) configuration dat


Please let me know if I need to check another thing...

---

