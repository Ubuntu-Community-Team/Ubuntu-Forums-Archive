---
title: "Yet ANOTHER &quot;Error activating XKB configuration&quot;"
date: 2009-10-24
forum: Hardware
---

### Post by brennon80 on 2009-10-24
I'm on a UK MacBook Pro.  I'm trying to change my keyboard layout to try and figure out how to type a stinkin' hash symbol (pound symbol).  I went to System > Preferences > Keyboard to try and change away from a default layout, selected MacBook/MacBook Pro (Intl) for the keyboard model, and was given this error:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10600000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

So, here are the results of those commands:

brennon@takemitsu:~$  xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "gb", "mac", ""
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "gb", "mac", ""

brennon@takemitsu:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 options = []
 model = macbook79

After searching the forums, I tried looking at /etc/X11/xorg.conf to edit the InputDevice section, but no such section exists.  Here are the contents of that file:

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Someone else fixed this problem by reinstalling xkb-data:

sudo aptitude reinstall xkb-data

This didn't help, either.  Another person solved the error with the following instructions:

Problem solved by going into gconf
desktop > gnome > peripherals > keyboard > general > host_computer > kbd
Then edit "layouts" and "options" and del everything.
Then you can set up a new keyboard in System, pref, keyboard.

Unfortunately, I have nothing entered for the layouts and options keys in gconf (as is obvious from the above gconf output). Another post suggested reconfiguring keyboard settings with:

sudo dpkg-reconfigure xserver-xorg

This didn't help, either.  In the process, though, I did find that I can print a hash symbol with the RIGHT Alt+3.  Left Alt+3 does nothing.  So, I've fied my initial problem, but still get these errors.  Does anyone have ANY ideas?  Google turns up an absolute SLEW of people with this error, but very, very few successful fixes.  ANY ideas would be greatly appreciated.  Thank you!

---

### Post by brennon80 on 2009-10-29
It's really strange to me that I see so many MacBooks running Ubuntu, and see this forum littered with people having had this same problem for years now, and no one has been able to address this yet...  Does anyone have an idea of the next thing I might try?  I'm not looking for a definite solution, just some ideas to try! ;)

---

