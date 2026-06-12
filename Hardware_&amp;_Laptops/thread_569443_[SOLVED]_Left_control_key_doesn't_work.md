---
title: "[SOLVED] Left control key doesn't work"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by sovereign_soul on 2007-10-07
Hi,

I have a problem here. All was fine till I installed the package "keytouch".  Since, I found that the package was useless, I removed it completely. However, now there's a problem - the left ctrl doesn't work anymore (rt ctrl works fine).

xev output for the left control key is 

KeyPress event, serial 29, synthetic NO, window 0x3400001,
    root 0x186, subw 0x0, time 12992526, (592,324), root:(597,397),
    state 0x0, keycode 235 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

the same for rt control key is 

KeyRelease event, serial 29, synthetic NO, window 0x3400001,
    root 0x186, subw 0x0, time 13285681, (628,323), root:(633,396),
    state 0x4, keycode 109 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

Seems that X no longer recognises the left control key. Is there any way to correct this by efiting some key map file ? if so then where is it located ?

I also checked different keyboard layout but no success. 

Thanks

[EDIT]
Solved - a restart was all that it needed :P

---

### Post by sovereign_soul on 2007-10-07
No reply ?? come on guys , there has to be some solution ..

---

