---
title: "Unrecognised hardware button on laptop"
date: 2009-12-31
forum: Hardware
---

### Post by nomadluap on 2009-12-31
Okay, I have this button on my Acer Aspire 5738 which is called the "program button" in the manual. When it is pressed, the 'p' turns green. That's it. I tried assigning it to open system monitor, but it was unrecognised. However, when I press it, my syslog spits out the following:

```
Dec 31 21:29:58 paul-laptop kernel: [10577.856074] atkbd.c: Unknown key pressed (translated set 2, code 0x8a on isa0060/serio0).
Dec 31 21:29:58 paul-laptop kernel: [10577.856080] atkbd.c: Use 'setkeycodes e00a <keycode>' to make it known.
Dec 31 21:29:58 paul-laptop kernel: [10577.862923] atkbd.c: Unknown key released (translated set 2, code 0x8a on isa0060/serio0).
Dec 31 21:29:58 paul-laptop kernel: [10577.862927] atkbd.c: Use 'setkeycodes e00a <keycode>' to make it known.
```So, does this mean that I should use 'sudo setkeycodes e00a <keycode> to assign it to something, such as "XF86PROGRAMKEY"?

---

