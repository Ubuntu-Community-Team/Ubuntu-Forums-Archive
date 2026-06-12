---
title: "Gutsy loses pressed left SHIFT/CTRL keys"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by dafi on 2007-12-26
I have a strange problem with keyboard and Gutsy.

When I press left SHIFT (or left CTRL) the pression status can be lost.
Suppose you press SHIFT to select text while selecting the text lose selection like you you have released the SHIFT key.
I've changed keyboard and the problem persists.
I press very strong the key and the problem persists.
Under Vista the problem never appears, NEVER!

What settings should cause problem with pressed keys?
Why only the LEFT Shift and Ctrl???????
any idea?

[COLOR="Red"]EDIT[/COLOR]

From xev WITHOUT any key pressed I receive movements from left shift and control, how is this possibile

KeyPress event, serial 30, synthetic NO, window 0x3600001,
    root 0x13a, subw 0x0, time 372040030, (-347,-283), root:(672,429),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3600001,
    root 0x13a, subw 0x0, time 372040030, (-347,-283), root:(672,429),
    state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x3600001,
    root 0x13a, subw 0x0, time 372050032, (-347,-283), root:(672,429),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3600001,
    root 0x13a, subw 0x0, time 372050032, (-347,-283), root:(672,429),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False




thanks in advance

---

### Post by dafi on 2008-01-02
Solved!!

The problem is due to xine that generates Left SHIFT and Left CTRL pressure events to avoid screensaver activation.

I've changed the timeout to a more reasonable value, the default is every  **_ten_** seconds.

1. open the ~/.xine/config file
2. search for gui.screensaver_timeout string
3. change the value (I've set 36000, 10 hours)

---

