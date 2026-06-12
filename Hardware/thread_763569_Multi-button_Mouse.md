---
title: "Multi-button Mouse"
date: 2008-04-23
forum: Hardware
---

### Post by Bal_Zac on 2008-04-23
Is there any way to bind mouse buttons to do certain actions without manually editing the xorg.conf file?  I guess I am lookig for a program to do this for me.

I have a mouse with the thumb buttons, and side scrolling middle mouse button.  However, I never use the middle scroll, so in windows I had it set so when I moved it left, it would be the same as pressing the middle mouse button, and moving the scroll right would be the same as a double click.  If anyone knows of a program to do this, that would be awesome.  Thanks!:guitar:

---

### Post by Bal_Zac on 2008-05-02
Wow don't everyone reply at once! J/k.  Well anywho, I ended up figuring out how to do this, so I figure I'll write a mini how to.

First off, I used the evdev driver for my mouse by adding the following into my xorg.conf file:
```

Section "InputDevice"
        Identifier      "Logitech MX400"
        Driver          "evdev"
EndSection

```
EDIT: Make sure that you put whatever you put for Identifier into the Section "ServerLayout" under InputDevice
```

Section "ServerLayout"
	Identifier	"Default Layout"
        screen "Default Screen"
	InputDevice     "Logitech MX400"
EndSection

```

After this, the command xev was showing up all 9 buttons.  For the Logitech MX400, the button assignments are as follows:
1 left click
2 middle click
3 right click
4 scroll up
5 scroll down
6 tilt left
7 tilt right
8 closest thumb button (back)
9 farthest thumb button (forward)

I then made 2 files, **.***middlekey* , and **.***doublekey* , and placed them in my *~* directory.  

**.**doublekey:
```
ButtonPress 1
ButtonRelease 1
ButtonPress 1
ButtonRelease 1
```

**.**middlekey:
```
ButtonPress 2
ButtonRelease 2
```

I then made a file, *.xbindkeysrc* , and again placed it in my *~* directory.

.xbindkeysrc:
```
"xmacroplay :0 < ~/.middlekey"
b:6
"xmacroplay :0 < ~/.doublekey"
b:7
```

Oddly enough in order to get the macro for the horizontal scroll to work, I had to run the following command:
```
xbindkeys -v -n
```

I'm guessing that Ubuntu is not setup by default to load the .xbindkeysrc file.  So, I made a small shell script:
```
#!/bin/sh
xbindkeys -v -n
```
which runs upon startup of gnome.  Simple as pie, right!

Also, I wanted to switch which thumb button performed back, and which performed forward.  So I made a file ***.**Xmodmap* , which I again placed in the ~ directory.

**.**Xmopmap:
```
pointer = 1 2 3 4 5 7 6 8 9
```

It wouldn't be too hard to write a program to do this all for you, so if anyone is actually interested, I'll write a quickey to do this for ya.

---

### Post by bladerunner6 on 2008-05-04
How do use this for my MX700 mouse in hardy heron

---

### Post by Bal_Zac on 2008-05-04
Use the command ***xev*** to see which buttons are assigned to which numbers.  A little white box will pop up, and press the buttons while your mosue is in the white box.  Then a bunch of stuff will pop up.  When I right click this pops up:

```
ButtonPress event, serial 31, synthetic NO, window 0x5200001,
    root 0x8b, subw 0x0, time 54248650, (146,125), root:(808,183),
    state 0x10, button 3, same_screen YES

ConfigureNotify event, serial 31, synthetic YES, window 0x5200001,
    event 0x5200001, window 0x5200001, (660,56), width 178, height 178,
    border_width 2, above 0x1201242, override NO

ButtonRelease event, serial 31, synthetic NO, window 0x5200001,
    root 0x8b, subw 0x0, time 54249042, (146,125), root:(808,183),
    state 0x410, button 3, same_screen YES
```

The important thing to note is that it says button 3, so my right click is assigned number 3.  Then in your .xbindkeysrc replace the button numbers with whatever button you want.

For example, if you wanted to make button 9 simulate a middle button click, and button 4 simulate a double click, then you .xbindkeysrc would be:
```
"xmacroplay :0 < ~/.middlekey"
b:9
"xmacroplay :0 < ~/.doublekey"
b:4
```

---

### Post by shimoda on 2008-05-04
I thing you could use **btnx**... It's easy and works perfect for me:
[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

---

### Post by Bal_Zac on 2008-05-06
You could use btnx, but where's the fun in that?  Manually editing config files FTW!

---

