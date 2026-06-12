---
title: "Ubuntu 12.10 laptop keyboard key 'T' working as Function F9. Not able to reset"
date: 2013-01-11
forum: Hardware
---

### Post by vivek146 on 2013-01-11
Hi All,

I use Ubuntu 12.10 on my Lenovo ideapad laptop (U300e). While working, i found that my **key 'T' (or 't') is working as F9**  :confused:. I didn't make any changes intensionally to do this.

Can you tell me how to fix this issue or to reset to my previous working condition.

Thanks,
vivek

**Note:** when i connect a USB keyboard to the laptop, the all the keys in external USB keyboard are working as expected with the same laptop.

---

### Post by vasiliscnisrok on 2013-01-11
1) run xev in Terminal
2) press key T and F9   give output here

my output
> KeyPress event, serial 41, synthetic NO, window 0x4a00001,
    root 0x28b, subw 0x0, time 17667889, (968,617), root:(1018,669),
    state 0x10, keycode 28 (keysym 0x74, t), same_screen YES,
    XLookupString gives 1 bytes: (74) "t"
    XmbLookupString gives 1 bytes: (74) "t"
    XFilterEvent returns: False

KeyRelease event, serial 41, synthetic NO, window 0x4a00001,
    root 0x28b, subw 0x0, time 17667967, (968,617), root:(1018,669),
    state 0x10, keycode 28 (keysym 0x74, t), same_screen YES,
    XLookupString gives 1 bytes: (74) "t"
    XFilterEvent returns: False

KeyPress event, serial 41, synthetic NO, window 0x4a00001,
    root 0x28b, subw 0x0, time 17680663, (968,617), root:(1018,669),
    state 0x10, keycode 75 (keysym 0xffc6, F9), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 41, synthetic NO, window 0x4a00001,
    root 0x28b, subw 0x0, time 17680728, (968,617), root:(1018,669),
    state 0x10, keycode 75 (keysym 0xffc6, F9), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


---

