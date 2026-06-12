---
title: "Logitech Office Internet multimedia keys"
date: 2009-01-22
forum: Hardware
---

### Post by fland on 2009-01-22
I'd installed keytouch and keytouch-editor, in keytouch I'd found my keyboard, but any changes in keys settings had no result. When I starting keytouch-editor I cann't get access to my keyboard, when I choosing any device, I am seeing window with "Please press one of the extra..." but pressing any multimedia key have no effect.
Maybe somebody knows different way to set up multimedia keys on this keyboard?

---

### Post by fland on 2009-01-23
bump

---

### Post by fland on 2009-01-25
when I am press some multimedia key in xev it generates such output:

KeyPress event, serial 31, synthetic NO, window 0x4000001,
    root 0x156, subw 0x0, time 3590568, (512,904), root: (519,955),
    state 0x10, keycode 152 (keysym 0x1008ff5d, XF86Explorer), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4000001,
    root 0x156, subw 0x0, time 3590774, (512,904), root: (519,955),
    state 0x10, keycode 152 (keysym 0x1008ff5d, XF86Explorer), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

but no XF86Explorer has been started. any ideas how it can be fixed?

---

