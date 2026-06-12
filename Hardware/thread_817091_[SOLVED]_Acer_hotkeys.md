---
title: "[SOLVED] Acer hotkeys"
date: 2008-06-03
forum: Hardware
---

### Post by Xbehave on 2008-06-03
how do i get my acer hotkeys to work ive looked all over but i find acer_acpi and a series of guides for acerhk. Im on a 64 bit system so cant user acerhk and cant fihure out what to do with acer acpi.

Im on an acer aspire 5101 (AWLMi) (AMD64).

THX

---

### Post by lok on 2008-06-03
I have pretty much the same laptop. If you havn't already, try setting the Keyboard Model to Acer Laptop in the System > Preferences > Keyboard > Layout tab. That worked for me. Good luck

---

### Post by Xbehave on 2008-06-03
Thanks ive set it to acer_laptop but the hotkeys still dont work :(

```
setxkbmap -model acer_laptop -layout gb
```
is what kdm is using :s

---

### Post by Xbehave on 2008-06-04
It turns out the problem was i was on 64bit, so i needed to install acerhk with a patch from the gentoo wiki.

---

