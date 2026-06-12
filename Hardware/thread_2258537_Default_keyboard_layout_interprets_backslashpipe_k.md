---
title: "Default keyboard layout interprets backslash/pipe key as &quot;&lt;&gt;&quot; key"
date: 2014-12-28
forum: Hardware
---

### Post by PercyAndrews on 2014-12-28
I just got a Lenovo ThnkPad 14, and installed Xubuntu on it.

I've used xmodmap, and it works, but it only runs after I log in, and I need this to be a low-level fix, because my password requires the use of the backslash/pipe key, so I currently have to use the onscreen keyboard to log in.

The default keyboard configuration is as follows, according to setxdbmap:

[FONT=courier new]$ setxkbmap -query -v 10
Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc102
layout:     us
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc+us+inet(evdev)
geometry:   pc(pc102)
rules:      evdev
model:      pc102
layout:     us[/FONT]

How should I go about fixing this (i.e. making backslash type backslash and shift-backslash type pipe)? Do I simply find a more appropriate keyboard configuration through trial and error? Or is there a quick adjustment I can make to /etc/default/keyboard that willl solve the problem?

Thanks for any help.

---

### Post by schragge on 2014-12-28
Are you sure this should be the pc102 keyboard model? It's an international keyboard model with <> key. Wouldn't the pc104 model be a better fit?

---

### Post by PercyAndrews on 2014-12-28
I honestly am not very familiar with different keyboard layouts, especially not enough to know them by name. But I tried pc104 and the issue still remains. Does that make any sense to you? setxkbmap -query -v 10 says model: 104, geometry: pc(pc104).

What should I do from here?

---

### Post by schragge on 2014-12-28
Well in */usr/share/X11/xkb/keycodes/evdev*: <LSGT> = 94 and <BKSL> = 51.
Check what keycode backslash key really generates on your keyboard with [xev -event keyboard](http://manpages.ubuntu.com/manpages/trusty/en/man1/xev.1.html) (It's a GUI program, but should be run from terminal).

---

### Post by PercyAndrews on 2014-12-28
It's 94. So how do I change what keycode it generates?
Also, would the 101-key layout be better than the 104 in principle? I looked at some pictures of the original keyboards and the 101 looks closer to what mine is. Of course, none of them solve the problem.

*edit: typo

---

### Post by schragge on 2014-12-28
Seems a bit strange, but try *classmate* as XKBMODEL. However, it repurposes right Ctrl as AltGr.

---

### Post by PercyAndrews on 2014-12-28
Is there no nifty little hack to simply tell it to associate a different keycode with that key, as there is with xmodmap? I might want to keep right Ctrl as it is...

---

### Post by schragge on 2014-12-29
Sure there is. But it's neither nifty nor little. See [here]("http://madduck.net/docs/extending-xkb/"). If you don't like messing with XKB rules then try to find a combination of ready-made model/layout/variant/options that fits you needs best.

A reasonable combination to try is
```

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="altgr-intl"
XKBOPTIONS="altwin:meta_alt"

```

---

### Post by PercyAndrews on 2014-12-31
I ended up figuring out a fix on my own; I modified /usr/share/X11/xkb/keycodes/evdev, replacing "<BKSL> = 51;" with "<BKSL> = 94;". It seems to work fine.

---

### Post by schragge on 2014-12-31
Fine, but be aware that */usr/share/X11/xkb/keycodes/evdev* will be overwritten on the next upgrade of xkb-data and your change will be lost.

---

