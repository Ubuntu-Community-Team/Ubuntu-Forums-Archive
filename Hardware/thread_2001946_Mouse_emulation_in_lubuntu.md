---
title: "Mouse emulation in lubuntu"
date: 2012-06-11
forum: Hardware
---

### Post by jake223 on 2012-06-11
I know there is an easy way to set up mouse emulation with the numpad in Xubuntu and Ubuntu. Is there an easy way to do so in lubuntu? is there a config file that can be edited, or does a program need to be installed?

---

### Post by papibe on 2012-06-11
Hi jake223.

I'm away from my Lubuntu laptop at the moment, but this is how it works in Ubuntu:

To activate the behaviour press:
```
Ctrl+Shift+NumLock
```
Then you can use the keypad to move the mouse: 8 up, 2 down, 4 left, and 6 right. You click using 5.

To disable it, press the same key combination that activates it.

Hope it helps,
Regards.

---

### Post by jake223 on 2012-06-11
That doesn't seem to work. I think it's for Gnome. ):

---

### Post by zombifier25 on 2012-06-11
Actually, AFAIK it's an X setting, not DE - specific. Run this command and post the output.
```
cat ~/.Xmodmap | grep Num
```

---

### Post by jake223 on 2012-06-12
> - Enable via conf file
Create a file /usr/share/X11/xorg.conf.d/90-enable-pointerkeys.conf, with contents:

Section "InputClass"
    Identifier             "Keyboard Defaults"
    MatchIsKeyboard        "yes"
    Option                 "XkbOptions" "keypad:__pointerkeys"
EndSection
- Enable for duration of session
setxkbmap -option keypad:__pointerkeys

In either case, Shift+Num-Lock will toggle mouse keys on/off.
-ixz at [COLOR="Blue"]_[askubuntu.com]("http://askubuntu.com/questions/149651/mouse-emulation-in-lubuntu")_[/COLOR]

:guitar:

---

