---
title: "Freeze"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by timreed on 2009-01-17
Anyone Know why Ubuntu all of a suddenly freezes.

---

### Post by aheckler on 2009-01-17
Could be a million reasons. Include some more details.

---

### Post by linux_tech on 2009-01-17
what are the system specs?
In terminal type
```
sudo lshw
```
try running memtest86 at boot to check the memory

---

### Post by thezood on 2009-01-17
> **timreed said:**
> Anyone Know why Ubuntu all of a suddenly freezes.
It's not even sure it WAS a freeze. If that happens, first try CTRL-ALT-Backspace that should restart X. If that doesn't work, you can go with REISUB. Hold CTRL-ALT-Print Screen/Sys Rq and press REISUB with small pauses between each one. That should safely reboot your computer. If THAT doesn't work, THEN you know it's truly a freeze. :)

---

### Post by sieve on 2009-01-26
> **thezood said:**
> It's not even sure it WAS a freeze. If that happens, first try CTRL-ALT-Backspace that should restart X. If that doesn't work, you can go with REISUB. Hold CTRL-ALT-Print Screen/Sys Rq and press REISUB with small pauses between each one. That should safely reboot your computer. If THAT doesn't work, THEN you know it's truly a freeze. :)

I'll have to try that.  My 8.10 ramdomly locks up also.

I had to look up what REISUB was though.  I'll post it here for the benefit of other ignorant folks like me ;)

> REISUB (Abbreviation) Reboot Even If System Utterly Broken. Typing REISUB while holding the Alt and SysRq keys is the way to reboot a locked up Linux system. 

---

### Post by sieve on 2009-02-15
I downloaded and installed a more recent video driver and have not had the freezing problem since.

And when it did freeze, ctrl-alt-backspace would not work and neither would REISUB.

---

