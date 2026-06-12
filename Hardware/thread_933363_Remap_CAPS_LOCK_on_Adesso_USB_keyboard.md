---
title: "Remap CAPS_LOCK on Adesso USB keyboard"
date: 2008-09-29
forum: Hardware
---

### Post by slackorama on 2008-09-29
I just bought a Adesso keyboard and am trying to remap the caps_lock on it.  But nothing seems to work.  I've tried "ctrl:nocaps" in my xorg.conf as well as using xmodmap. I've done this zillions of times before on other keyboards.

To my untrained eye, it seems like an event ordering problem.  Using the "normal" control character, four events are sent in this order:  press ctrl, press 'c', release 'c', release 'ctrl.'  This is what I expect would happen.

However, using a remapped capslock key, the four events are: press ctrl, release ctrl, press 'c', release 'c'.  This is what confuses me.  Any  ideas or suggestions on what I may be able to do to fix this, or come up with some sort of a workaround?  Is this a hardware issue?

Thanks in advance.

My xmodmap commands:
```

  clear Lock
  keycode 66 = Control_L
  add control = Control_L

```

Here are the xev reports for a "normal" control key:

```

    KeyPress event, serial 31, synthetic NO, window 0x1100001,
        root 0x1f0, subw 0x0, time 2428520, (121,111), root:(2470,722),
        state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
        XLookupString gives 0 bytes:
        XmbLookupString gives 0 bytes:
        XFilterEvent returns: False

    KeyPress event, serial 31, synthetic NO, window 0x1100001,
        root 0x1f0, subw 0x0, time 2430328, (121,111), root:(2470,722),
       state 0x4, keycode 54 (keysym 0x63, c), same_screen YES,
        XLookupString gives 1 bytes: (03) ""
        XmbLookupString gives 1 bytes: (03) ""
        XFilterEvent returns: False

    KeyRelease event, serial 31, synthetic NO, window 0x1100001,
        root 0x1f0, subw 0x0, time 2430384, (121,111), root:(2470,722),
        state 0x4, keycode 54 (keysym 0x63, c), same_screen YES,
        XLookupString gives 1 bytes: (03) ""

    KeyRelease event, serial 31, synthetic NO, window 0x1100001,
        root 0x1f0, subw 0x0, time 2432808, (121,111), root:(2470,722),
        state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
        XLookupString gives 0 bytes:

```

However, for the remapped capslock, I get this:

```

KeyPress event, serial 31, synthetic NO, window 0x1100001,
    root 0x1f0, subw 0x0, time 2435112, (121,111), root:(2470,722),
    state 0x0, keycode 66 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x1100001,
    root 0x1f0, subw 0x0, time 2435936, (121,111), root:(2470,722),
    state 0x4, keycode 66 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes:

KeyPress event, serial 31, synthetic NO, window 0x1100001,
    root 0x1f0, subw 0x0, time 2435936, (121,111), root:(2470,722),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"
    XmbLookupString gives 1 bytes: (63) "c"
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x1100001,
    root 0x1f0, subw 0x0, time 2436008, (121,111), root:(2470,722),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"

```

---

### Post by slackorama on 2008-10-06
*sigh*  Anyone?

---

### Post by arch_o_median on 2009-08-24
Hi Slackorama.   I have a Microsoft Comfort Curve 2000 V1.0 USB keyboard.   It is plugged into my laptop where I have modified xmodmap to swap caps lock and the left control key.  Unfortunately this remapping does not seem to effect the USB keyboard lay out.  :-(
  Have you had any luck with this issue?

---

### Post by slackorama on 2009-08-24
> **arch_o_median said:**
> Have you had any luck with this issue?

I haven't.  I ended up giving the keyboard to my buddy who recommended it to me.  I suspect it was a ploy on his part to get a new keyboard.  

Sorry.

---

