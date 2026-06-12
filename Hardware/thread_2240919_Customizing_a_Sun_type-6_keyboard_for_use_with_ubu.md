---
title: "Customizing a Sun type-6 keyboard for use with ubuntu"
date: 2014-08-23
forum: Hardware
---

### Post by cjsmall on 2014-08-23
I am configuring a new Xeon-based xubuntu 14.04 system and would like to use a Sun USB 3-button mouse and type-6 keyboard.  I have these plugged in and they generally work.  However, many of the special keys on the keyboard are not issuing keycodes that are being received as escape codes by the system.  I have been using these blocks of keys for special purposes and am pretty much lost without them working. So, before I reinvent the wheel, I wanted to see if anyone had tackled this problem and had a working solution.

BTW, the current xkeycaps package (2.47.4) does not include definitions for the type-6 keyboard.  There is a type-5 kbd, but even though the layout is identical, not even the standard keys correspond to highlighted keys on the screen.

I have found these keyboards to be the most comfortable, but if there is no good solution for mapping the keys, I would be happy to hear recommendations for alternative keyboards others are using that have a standard UNIX layout, a full keypad to the right, and hopefully and additional block of keys to the left.

Thanks for any light you can shed on this problem!  :-)

---

### Post by xanias on 2014-08-24
You can use the following command:

> sudo dpkg-reconfigure keyboard-configuration

Then just scroll down to the sun keyboard layouts and use the one that suits you best, there's a type-6 configuration available. You can then define shortcuts (Settings->Keyboard->Shortcuts) to taste.

---

### Post by cjsmall on 2014-08-24
xanias, thank you for that very useful piece of information.  I had found the Keyboard option on the Settings Manager and selected the Sun Type 6  USB (Unix Layout), but your command seems to offer more options.  Unfortunately, after running the command, many of the keyboard keys (the entire left block, Insert, and a number of others) are not sending events to the system -- or more likely, the system is trapping them and not passing them on to the application layer.  For example, the desktop manager appears to be trapping the Print Screen and Compose keys and performing operations rather than passing these keycodes on.  Possible this is what happens with the other non-functioning keys.

So any further suggestions on how to take this a step further and gain complete control over the keyboard?

---

