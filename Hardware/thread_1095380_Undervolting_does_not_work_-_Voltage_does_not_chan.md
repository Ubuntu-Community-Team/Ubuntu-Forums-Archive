---
title: "Undervolting does not work - Voltage does not change"
date: 2009-03-13
forum: Hardware
---

### Post by Daniel_le_Rouge on 2009-03-13
Hey everybody,

I have recently switched from Vista to ubuntu and I still have problems with my battery.

Now I want to undervolt my processor - an Intel Core 2 in a Fujitsu-Siemens Amilo Pi 2530. I successfully patched the kernel and installed PHC-Tool with its GUI. This works out fine, but when I change the processors' voltage (VID) nothing happens. The default values rest (see attached screenshot).

What am I making wrong and what changes are necessary to let it work?

Thanks for any help!

Daniel

---

### Post by mister_playboy on 2009-04-07
It seem most Core 2 Duo and Pentium Dual-Core processors can't be set to a VID lower than 19.

No biggie... just set 19 across the board and you are good to go.  It's still much cooler than stock.

---

### Post by inso_741 on 2010-04-25
how did u patch the kernel?
did u recompile it? or just patched the running kernel?

---

