---
title: "Gateway E295C special laptop keys under monitor not working"
date: 2010-04-02
forum: Hardware
---

### Post by TygerFish on 2010-04-02
I have a Gateway E295C/C140/M290.  It's a tablet PC, which has its own set of challenges, but this one in particular is about the keys underneath the monitor (see attached picture).

Ordinarily, these keys do not seem to be registered as X events using *xev* -- that is, no output is generated in xev when I press these keys.

The only time they do anything at all in Linux is when I press one of the four buttons on the left of the D-pad first.  Then, pressing up or down on the D-pad will mimic the behavior of Fn-up/down, which is to adjust the monitor brightness.  For example, a-b-c-[Ddown]-[Dup]-1-2-3 will produce:
```
KeyPress event, serial 35, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24981625, (1210,574), root:(1213,595),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XmbLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24981752, (1210,574), root:(1213,595),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24981987, (1210,574), root:(1213,595),
    state 0x0, keycode 56 (keysym 0x62, b), same_screen YES,
    XLookupString gives 1 bytes: (62) "b"
    XmbLookupString gives 1 bytes: (62) "b"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24982070, (1210,574), root:(1213,595),
    state 0x0, keycode 56 (keysym 0x62, b), same_screen YES,
    XLookupString gives 1 bytes: (62) "b"
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24982410, (1210,574), root:(1213,595),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"
    XmbLookupString gives 1 bytes: (63) "c"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24982506, (1210,574), root:(1213,595),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"
    XFilterEvent returns: False

MappingNotify event, serial 35, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 35, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 247

FocusOut event, serial 35, synthetic NO, window 0x4600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 35, synthetic NO, window 0x4600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 37, synthetic NO, window 0x4600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 37, synthetic NO, window 0x4600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 37, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

MappingNotify event, serial 37, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 37, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 247

KeyPress event, serial 37, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24988271, (1210,574), root:(1213,595),
    state 0x0, keycode 10 (keysym 0x31, 1), same_screen YES,
    XLookupString gives 1 bytes: (31) "1"
    XmbLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False

KeyRelease event, serial 39, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24988377, (1210,574), root:(1213,595),
    state 0x0, keycode 10 (keysym 0x31, 1), same_screen YES,
    XLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False

KeyPress event, serial 39, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24988636, (1210,574), root:(1213,595),
    state 0x0, keycode 11 (keysym 0x32, 2), same_screen YES,
    XLookupString gives 1 bytes: (32) "2"
    XmbLookupString gives 1 bytes: (32) "2"
    XFilterEvent returns: False

KeyRelease event, serial 39, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24988721, (1210,574), root:(1213,595),
    state 0x0, keycode 11 (keysym 0x32, 2), same_screen YES,
    XLookupString gives 1 bytes: (32) "2"
    XFilterEvent returns: False

KeyPress event, serial 39, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24988972, (1210,574), root:(1213,595),
    state 0x0, keycode 12 (keysym 0x33, 3), same_screen YES,
    XLookupString gives 1 bytes: (33) "3"
    XmbLookupString gives 1 bytes: (33) "3"
    XFilterEvent returns: False

KeyRelease event, serial 39, synthetic NO, window 0x4600001,
    root 0x65, subw 0x0, time 24989083, (1210,574), root:(1213,595),
    state 0x0, keycode 12 (keysym 0x33, 3), same_screen YES,
    XLookupString gives 1 bytes: (33) "3"
    XFilterEvent returns: False

```

I'm not sure what it means but the "serial" value only seems to increase as a result of these D-keys, and only when another key has been pressed in between presses of that D-key.  For example:
```
<startup>  serial 48
[a]        serial 51
[b]        serial 51
[Dup]      serial 51
[Dup]      serial 51
[Ddown]    serial 53
[Dup]      serial 53
[a]        serial 55
[1]        serial 55
[Dup]      serial 55
[a]        serial 57
```

I'm not sure what this means, but they only seem to be recognized if they activate as monitor brightness keys.

What else can I do to help get these keys recognized so that I can assign functions to them?

---

