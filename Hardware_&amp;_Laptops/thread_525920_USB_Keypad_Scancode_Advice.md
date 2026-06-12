---
title: "USB Keypad Scancode Advice"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by cdrom600 on 2007-08-14
Hi.

I do a fair amount of Spanish typing, and it quickly becomes a pain to do something special to insert accented and special characters (áéíóúñ«»¿¡).  To resolve this, I've mapped my number pad keys to these special characters (I'll include my .Xmodmap file below).  However, this means that I can't use the number pad normally now.

I'm thinking that unless I can find a solution which will do something like only replace the numbers when Num Lock is off, my best option is to buy a cheap USB keypad that spits out the keycodes 10-19 (the same ones as the number row on top of the keyboard) rather than the 79-90 that the number pad uses.

The theory is that the number pad built on my keyboard will continue to spit out keycodes 79-90 and give me my special characters, while the USB keypad and the number row would act as normal numbers.  I have three questions, then:

1) Is there any solution to only replace my number keys when Num Lock is off?
2) Is my theory that a USB keypad would work the same as my number row correct, assuming the keypad spits out the scancodes 10-19?
3) I need to figure out a keypad model that gives scancodes 10-19 rather than 79-90.
**If you have a USB number keypad,** please open a terminal, run ```
xev
``` and press the number 1 on the keypad.  If the output looks like:
```
KeyRelease event, serial 29, synthetic NO, window 0x4c00001,
    root 0x186, subw 0x0, time 14945806, (81,-14), root:(96,107),
    state 0x10, **keycode 10** (keysym 0x31, 1), same_screen YES,
    XLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False
```
then that's what I'm looking for.  If it returns
```
KeyPress event, serial 29, synthetic NO, window 0x4c00001,
    root 0x186, subw 0x0, time 14995787, (236,89), root:(251,210),
    state 0x10, **keycode 87** (keysym 0xab, guillemotleft), same_screen YES,
    XLookupString gives 2 bytes: (c2 ab) "«"
    XmbLookupString gives 2 bytes: (c2 ab) "«"
    XFilterEvent returns: False
```
then it's not what I'm looking for.

Thanks.

```
$ cat ~/.Xmodmap
keycode 79 = aacute
keycode 80 = eacute
keycode 81 = iacute
keycode 83 = oacute
keycode 84 = uacute
keycode 85 = ntilde
keycode 87 = guillemotleft
keycode 88 = guillemotright
keycode 89 = questiondown
keycode 90 = exclamdown
```

---

