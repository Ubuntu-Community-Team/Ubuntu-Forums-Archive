---
title: "I'd really appreciate some assistance getting my MUTE (F11) key to work."
date: 2011-01-29
forum: Hardware
---

### Post by inverser on 2011-01-29
The F11 key itself works, but when I press Fn+F11, which is the mute function, the keyboard stops responding. I have to sleep the machine and wake it up to regain keyboard control. And sound doesn't get muted either. Also, strangely, the LED underneath the key is always lit, which should mean sound is muted. This is weird because the LED for caps lock, WiFi and number lock functions just fine and the LED indicator toggles appropriately. 

Anyway, I've googled for hours on end trying to find a fix for it, but I've not come up with anything. Any ideas?

My laptop is a Voodoo Envy 133.

xev output for F11:

```
KeyPress event, serial 36, synthetic NO, window 0x5400001,
    root 0xac, subw 0x0, time 6536115, (502,-375), root:(505,220),
    state 0x0, keycode 95 (keysym 0xffc8, F11), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x5400001,
    root 0xac, subw 0x0, time 6536229, (502,-375), root:(505,220),
    state 0x0, keycode 95 (keysym 0xffc8, F11), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 36, synthetic NO, window 0x5400001,
    mode NotifyNormal, detail NotifyNonlinear

```

xev output for Fn+F11 (MUTE):

```
FocusOut event, serial 36, synthetic NO, window 0x5400001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 36, synthetic NO, window 0x5400001,
    mode NotifyWhileGrabbed, detail NotifyNonlinear

FocusOut event, serial 36, synthetic NO, window 0x4200001,
    mode NotifyGrab, detail NotifyAncestor
```

---

### Post by inverser on 2011-01-31
Really? No one has the expertise to help me out here? How do I reconfigure the LED to toggle correctly? How do I assign mute to Fn+F11?

---

### Post by sam1948 on 2011-01-31
hi, 
i m really not sure but u can try this:
in the menu: System->Preferences->Keyboard Shortcuts

find the mute, select it, and press the combination u like.

if it is already assigned to disabling keyboard, ubuntu will ask u if u want to cancel that. approve and i hope it will work

---

### Post by inverser on 2011-01-31
> **sam1948 said:**
> hi, 
i m really not sure but u can try this:
in the menu: System->Preferences->Keyboard Shortcuts

find the mute, select it, and press the combination u like.

if it is already assigned to disabling keyboard, ubuntu will ask u if u want to cancel that. approve and i hope it will work

Thanks for the reply, man. I tried that but hitting Fn+11 just locks out the keyboard.

---

