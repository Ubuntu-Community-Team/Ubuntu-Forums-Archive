---
title: "Ubuntu on Yoga need screen rotation to work"
date: 2016-12-31
forum: Hardware
---

### Post by Monsuco on 2016-12-31
I'm tinkering with an older model of Lenovo Yoga I was given. It works, but there are three quirks with it that I can't seem to figure out.
[LIST=1]
[*]How do I get screen rotation to work?
[*]How do I get an on-screen keyboard to come up when I have the device folded into "tablet mode" and touch a text entry field?
[*]How do I disable the touchpad mouse when it's folded into tablet mode? (It is smart enough to disable the keyboard).
[/LIST]
Those were issues I encountered right off the bat. I'd rather use Linux than Windows 10 on this thing if possible.

---

### Post by hanspeteriv on 2017-01-01
To get the onscreen keyboard and automatically hide it when you are not in a text field:
 -Go to system Settings > Universal Access > Typing and enable the On Screen Keybaord option.
 -Click the new icon in your system tray and select Preferences.
 -Find and enable auto hide/show. You probably also want to enable the option to not show the onscreen keyboard while you are using the hardware keyboard.


I assume you want to rotate the screen 180° when folding your device into tablet mode, not auto-rotate the screen to portrait/landscape mode when you rotate the device.

If you modify the script from this answer on askubuntu and run it after switching between tablet and normal mode that should work for you. [1][INDENT]Because the keyboard is enabled in normal mode and disabled in tablet mode you would want a script that does this:

if the keyboard is disabled (aka if you switched into tablet mode)[/INDENT]
[INDENT=2]-disable the touchpad
 -rotate your screen and touchscreen input 180°[/INDENT]
[INDENT]
 if the keyboard is enabled (aka if you switched into normal mode)[/INDENT]
[INDENT=2]-enable the touchpad
 -rotate the screen and touchscreen input back to normal[/INDENT]
[INDENT]
To modify the script you will need the names of your xinput devices for keyboard, touchscreen and touchpad. You can find the names of your devices with
```
xinput --list
```[/INDENT]
[INDENT]
[/INDENT]

[1] [https://askubuntu.com/questions/450066/rotate-touchscreen-and-disable-the-touchpad-on-yoga-2-pro-in-rotated-mode/485685#485685](https://askubuntu.com/questions/450066/rotate-touchscreen-and-disable-the-touchpad-on-yoga-2-pro-in-rotated-mode/485685#485685)

---

