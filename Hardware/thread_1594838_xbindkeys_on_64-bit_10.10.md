---
title: "xbindkeys on 64-bit 10.10"
date: 2010-10-12
forum: Hardware
---

### Post by JSHarrison on 2010-10-12
I have installed xbindkeys on my new 10.10 install and cannot seem to get any of my key bindings to respond. I have the following block of code in my .xbindkeysrc file:

```

#insert email from ctrl shift e
"xte 'str email'"
    m:0x15 + c:37
    Control+Shift+Mod2 + Control_L

```

The idea is that Ctrl+Shift+E will insert my email address. I have restarted xbindkeys after editing .xbindkeysrc but nothing happens when I press the key combination. What am I missing?

---

