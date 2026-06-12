---
title: "Different keys have the same keycode in xev. Can I change keycodes?"
date: 2009-03-27
forum: Hardware
---

### Post by riwa on 2009-03-27
I have a gaming keyboard: A4TECH X7 G800 where most buttons work fine.

But there are some gamer specific buttons (+-*/'å",.ö,) that give this output. They have the same keycode as their corresponding symbol and, of course, produce the same output. 

But these buttons could be very useful to me (mostly in games) so I wish to change the keycodes or keysyms or whatever. 

This is the output of xev:

```
KeyPress event, serial 30, synthetic NO, window 0x3200001,
    root 0x2ed, subw 0x0, time 15150753, (67,88), root:(71,677),
    state 0x0, keycode 60 (keysym 0x2e, period), same_screen YES,
    XLookupString gives 1 bytes: (2e) "."
    XmbLookupString gives 1 bytes: (2e) "."
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3200001,
    root 0x2ed, subw 0x0, time 15150878, (67,88), root:(71,677),
    state 0x0, keycode 60 (keysym 0x2e, period), same_screen YES,
    XLookupString gives 1 bytes: (2e) "."
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x3200001,
    root 0x2ed, subw 0x0, time 15153632, (67,88), root:(71,677),
    state 0x0, keycode 60 (keysym 0x2e, period), same_screen YES,
    XLookupString gives 1 bytes: (2e) "."
    XmbLookupString gives 1 bytes: (2e) "."
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3200001,
    root 0x2ed, subw 0x0, time 15153735, (67,88), root:(71,677),
    state 0x0, keycode 60 (keysym 0x2e, period), same_screen YES,
    XLookupString gives 1 bytes: (2e) "."
    XFilterEvent returns: False

```

The top two refers to the button G9 and the bottom two refers to .(period).

As they appear to be identical I cannot see how to change the value of one of them alone. 

Thanks in advance.

/Richard

Edit: I just noticed (as you probably will) that the serial is different. For what it's worth.

---

### Post by universe on 2010-02-26
Anyone found a solution for that?
I'm facing the same problem with Logitech Cordless Desktop Wave Pro keyboard.

Two keys with same keycode but different serial.

Would be nice to use both for different applications!

Cheers,
Bernhard.

---

