---
title: "Asus F3E blue keys don't work"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by zbyszek on 2008-03-01
After installing 7.10 on my Asus F3E I find out that
1. Wireless (turn on and off), 3D graphics, dual monitor, douchpad is just working
1a, Blue keys: wireless, numlock, switch monitor works ok.
2. Webcam,  do not work.
3. Blue (hot) keys: slepp, mail, web, brightness up and down, don't work
4. Blue keys volume up and volume down work improperly


Any help will be appreciated



xev shows that some keys are not definedxev shows that some keys are not defined


KeyPress event, serial 28, synthetic NO, window 0x3c00001,
    root 0x67, subw 0x0, time 1763809554, (-178,483), root:(921,507),
    state 0x0, keycode 236 (keysym 0x1008ff19, XF86Mail), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 28, synthetic NO, window 0x3c00001,
    root 0x67, subw 0x0, time 1763809554, (-178,483), root:(921,507),
    state 0x0, keycode 236 (keysym 0x1008ff19, XF86Mail), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x3c00001,
    root 0x67, subw 0x0, time 1763809919, (-178,483), root:(921,507),
    state 0x0, keycode 178 (keysym 0x1008ff2e, XF86WWW), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3c00001,
    root 0x67, subw 0x0, time 1763809919, (-178,483), root:(921,507),
    state 0x0, keycode 178 (keysym 0x1008ff2e, XF86WWW), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x3c00001,
    root 0x67, subw 0x0, time 1763809937, (-178,483), root:(921,507),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3c00001,
    root 0x67, subw 0x0, time 1763809937, (-178,483), root:(921,507),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x3c00001,
    root 0x67, subw 0x0, time 1763809951, (-178,483), root:(921,507),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3c00001,
    root 0x67, subw 0x0, time 1763809951, (-178,483), root:(921,507),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

---

