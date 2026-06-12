---
title: "Remap the Insert key"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by c.ovidiu on 2008-02-07
Hi. I have a compact keyboard that does not have a right Ctrl key, but has an Insert key instead. I want to map that Insert key to act like a right Ctrl. I entered this in my .bashrc:

xmodmap -e "keycode 106 = Control_R"

Now when I fire up xev in the console and press that Insert key, I get the following:

```
KeyPress event, serial 31, synthetic NO, window 0x3000001,
    root 0x1a5, subw 0x0, time 4124484653, (-466,68), root:(193,116),
    state 0x0, keycode 106 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False
```

When I press the left Ctrl key, I get:

```
KeyRelease event, serial 32, synthetic NO, window 0x3000001,
    root 0x1a5, subw 0x0, time 4124528865, (-288,190), root:(371,238),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```

The problem is, the Insert key doesn't really behave like a Ctrl. For example if I press Insert-Shift-T in gnome-terminal I don't get a new tab, I just get the letter “T”. Any ideas?

---

### Post by c.ovidiu on 2008-02-08
Anyone?

---

