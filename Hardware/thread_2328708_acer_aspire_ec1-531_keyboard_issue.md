---
title: "acer aspire ec1-531 keyboard issue"
date: 2016-06-23
forum: Hardware
---

### Post by cyril6 on 2016-06-23
Hi all,

I have a persistant issue. I have try litteraly everything I can.

But I can't get CTRL + ALT + 2 or 3 or 4 etc to work CTRL + ALT + T work fine but I can't get any special caractere.

Shift+ 2 works for example and gives me "
Shift+ 3 = *
etc.

My laptop is an acer aspire es1-531 with a Swiss French Keyboard on Lubuntu 16.04

Anyone got an idea?

thanks,

CAA

---

### Post by cyril6 on 2016-06-23
if I do xev in the terminal strangely when I press CTRL + ALT + 2 I see ^@

KeyPress event, serial 45, synthetic NO, window 0xc00001,
    root 0xf6, subw 0x0, time 1164116, (232,-175), root:(233,267),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 48, synthetic NO, window 0xc00001,
    root 0xf6, subw 0x0, time 1164133, (232,-175), root:(233,267),
    state 0x14, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 48, synthetic NO, window 0xc00001,
    root 0xf6, subw 0x0, time 1164283, (232,-175), root:(233,267),
    state 0x1c, keycode 11 (keysym 0x32, 2), same_screen YES,
    XLookupString gives 1 bytes: (00) ""
    XmbLookupString gives 1 bytes: (00) ""
    XFilterEvent returns: False


KeyRelease event, serial 48, synthetic NO, window 0xc00001,
    root 0xf6, subw 0x0, time 1164410, (232,-175), root:(233,267),
    state 0x1c, keycode 11 (keysym 0x32, 2), same_screen YES,
    XLookupString gives 1 bytes: (00) ""
    XFilterEvent returns: False


KeyRelease event, serial 48, synthetic NO, window 0xc00001,
    root 0xf6, subw 0x0, time 1164647, (232,-175), root:(233,267),
    state 0x1c, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 48, synthetic NO, window 0xc00001,
    root 0xf6, subw 0x0, time 1164656, (232,-175), root:(233,267),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

So I'm guessing its not an hardware problem... 

Would very much appreciate if someone could help me resolve this issue 

thanks again,

CAA

---

