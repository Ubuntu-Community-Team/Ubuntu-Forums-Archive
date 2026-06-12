---
title: "Dell Inspiron 14z - Questions about three shortcut buttons above keyboard"
date: 2012-01-16
forum: Hardware
---

### Post by milosz.galazka on 2012-01-16
Hello,

Dell Inspiron 14z has three small shortcut buttons above keyboard.
First with small gears is OK as it is reconized by xev:

```

KeyRelease event, serial 35, synthetic NO, window 0x2600001,
    root 0x64, subw 0x0, time 3779727, (223,572), root:(717,595),
    state 0x40, keycode 53 (keysym 0x78, x), same_screen YES,
    XLookupString gives 1 bytes: (78) "x"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x2600001,
    root 0x64, subw 0x0, time 3779731, (223,572), root:(717,595),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

Second with wrench on it. There is no output in dmesg, xev, showkey and evtest when it is pressed. Can it be used somehow?

Third one with a small star. Dmesg output shows:

```
atkbd serio0: Use 'setkeycodes 60 <keycode>' to make it known.
```

So I tried:

```
setkeycodes 60 247
```

[getscancodes]("http://sourceforge.net/projects/keytouch/files/getscancodes/getscancodes%201.0/") shows:

```
96 (0x60)
```

Then mapped it using xmodmap:

```
keycode 255 = XF86Launch1
```

But there is a problem. It is reconized only first time I use it.
xev just loops until I press any key:

```
KeyRelease event, serial 35, synthetic NO, window 0x2600001,
    root 0x64, subw 0x0, time 4300406, (-89,542), root:(405,565),
    state 0x0, keycode 255 (keysym 0x1008ff41, XF86Launch1), same_screen YES,
    XKeysymToKeycode returns keycode: 156
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

showkey shows that there is no key release:

```
press any key (program terminates 10s after last keypress)...
keycode  28 release
keycode 247 press
keycode 247 press
keycode 247 press
```

evtest shows value 1 after pressing it first time, value 2 afterwards:

```
Event: time 1326753132.767858, -------------- Report Sync ------------
Event: time 1326753134.329820, type 4 (Misc), code 4 (ScanCode), value 60
Event: time 1326753134.329841, type 1 (Key), code 247 (RF kill), value 1
Event: time 1326753134.329842, -------------- Report Sync ------------
Event: time 1326753137.387821, type 4 (Misc), code 4 (ScanCode), value 60
Event: time 1326753137.387842, type 1 (Key), code 247 (RF kill), value 2

```

Is there a way to make it work?

Thanks,
milosz

//edit

I use Ubuntu 11.10, kernel:
Linux 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

I also tried without success using:
```
setkeycodes 60 222
```

// update 20 Jan 2012

After editing xserver-xorg-input-evdev source package and compiling it I managed to get third button (with small star on it) working using some code from this [place]("https://github.com/dgolda/maxter-plus-linux/commit/d7a0bbb5c27d58a7da99884b2b93abff403dc9f5#xserver-xorg-input-evdev-2.3.2/src/evdev.c") as solution is very similar. I will try to describe it after weekend.

So the last question is: Is it possible somehow to use second button with wrench on it (it doesn't send anything)?
I don't even know where to start searching.

---

### Post by milosz.galazka on 2012-01-19
bump

---

