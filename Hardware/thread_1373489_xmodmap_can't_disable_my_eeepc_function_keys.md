---
title: "xmodmap can't disable my eeepc function keys"
date: 2010-01-05
forum: Hardware
---

### Post by gcbzzzz on 2010-01-05
trying to disable my function key for sleepmode, i'm trying first to disable the volume keys to ease testing.

```
$ xmodmap -pke | grep -i volume
keycode 122 = XF86AudioLowerVolume NoSymbol XF86AudioLowerVolume NoSymbol XF86AudioLowerVolume
keycode 123 = XF86AudioRaiseVolume NoSymbol XF86AudioRaiseVolume NoSymbol XF86AudioRaiseVolume

$ xmodmap -e 'keycode 122 = NoSymbol'
```


now I press the volume down key, and the volume goes down. What am I doing wrong?

here's the xev output. I can't make sense of it to get a keycode.
```

MappingNotify event, serial 31, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 31, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 247

FocusOut event, serial 31, synthetic NO, window 0x4000001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x4000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

MappingNotify event, serial 33, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 33, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 247

```

thanks for any help!

would be great to have a GUI app for that :)

---

edit: solved

I still can't make head or tails of the xev output, but putting the xmodmap string on ~/.Xmodmap solved it after I restarted my X session.

for the eeepc 1000 i used:
keycode 150 = F20

now the sleep key don't mess my wifi/randomly crashs the whole machine. :D

i still can't find on the manpages when exactly the modmap is taken into effect. but if i open an xterm, execute an xmodmap, and then open an xterm inside that xterm, the xmodmap change takes effect, but not on other windows...

---

