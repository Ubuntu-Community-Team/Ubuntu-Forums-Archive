---
title: "netbook xmodmap question"
date: 2009-04-24
forum: Hardware
---

### Post by mrvanes on 2009-04-24
Hi,

I've been banging my head against the keyboard over this problem: I recently bought a B-brand netbook with all the standard features. The keyboard layout is decent, but they decided to combine arrow keys and home/end/pgup/pgdown. I couldn't get these to work untill I discovered they are activated by shift.
The problem now is that the home/end/pgup/pgdown keys are shift_modified according to X, which is true if you look at the xev output for home (shift+Left)

```
KeyPress event, serial 31, synthetic NO, window 0x3600001,
    root 0xc9, subw 0x0, time 11089562, (396,-7), root:(400,411),
    state 0x0, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x3600001,
    root 0xc9, subw 0x0, time 11089683, (396,-7), root:(400,411),
    state 0x1, keycode 110 (keysym 0xff50, Home), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3600001,
    root 0xc9, subw 0x0, time 11089736, (396,-7), root:(400,411),
    state 0x1, keycode 110 (keysym 0xff50, Home), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3600001,
    root 0xc9, subw 0x0, time 11090159, (396,-7), root:(400,411),
    state 0x1, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```

So I decided that shift+Home should be mapped to Home as well using this xmodmap command:

```
xmodmap -e "keycode 110 = Home Home Home NoSymbol Home"
```

I now expect the 2nd modifier for keycode 110 to generate the Home event, but it doesn't work. I get an H (shift+Home) instead of a Home event, probably because the generated Home event is still shift modified (which is true).

So, how do I un-shift the Home event, while the shift key is pressed to generate it?

Another solution I thought of was to discard the manufacturers solution and generate Home on ctrl+Left (keycode 113) but now it turns out I can't generate ctrl modified events. It should be the third parameter of the xmodmap -e command, but when I do this:

```
xmodmap -e "keycode 10 = 1 2 3 4 5"
```
I would expect key 1 to generate a "1" (true) shift+1 a "2" (true) and ctrl+1 a "3" (not true, I get a "1").

But the ctrl modifier is correctly configured (xev code for left ctrl is 0x25 and right_ctrl is 0x69)

```
# xmodmap -pm
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

```

Can anybody shed a light on this please? What am I missing?

---

### Post by jamessnell on 2009-04-24
You have my sympathy.. I'm sure someone can help with that.. I'd just have to google a bunch to figure it out myself, maybe the xorg man page would be helpful. 

Good luck!

---

### Post by mrvanes on 2009-04-29
I hate to do this, but is there really no one that might have a clue how to go about this?

*bump*

---

### Post by jamessnell on 2009-04-29
> **mrvanes said:**
> I hate to do this, but is there really no one that might have a clue how to go about this?

*bump*

Well, the beauty of Linux is that if you're actually the first person with a particular problem, you're welcome to implement a solution and submit it to whatever the appropriate project is for general use.

All I can really suggest is reading the Xorg documentation... I'd expect there to be something rather helpful there. 

Good luck.

---

### Post by mrvanes on 2009-04-30
> **jamessnell said:**
> All I can really suggest is reading the Xorg documentation... I'd expect there to be something rather helpful there.
Believe me, I did... this was my last resort... :(

---

