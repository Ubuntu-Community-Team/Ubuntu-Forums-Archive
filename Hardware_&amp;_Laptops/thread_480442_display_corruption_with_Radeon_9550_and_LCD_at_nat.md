---
title: "display corruption with Radeon 9550 and LCD at native res"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by Ex-Cyber on 2007-06-21
I just installed Ubuntu 7.04, and when I set the screen resolution to my LCD monitor's native resolution (1440x900), a strange kind of corruption occurs. There is a kind of overlap effect with the leftmost and rightmost regions of the screen - if something draws in one of these regions, a corrupted version of what was drawn appears in the other. This only happens at 1440x900 - other resolutions, including other widescreen resolutions, are not affected. Anyone know what's going on?

---

### Post by Ex-Cyber on 2007-07-07
This seems to be fixed by changing the "1440x1050" to "1440x900" and adding the line
```
Virtual 1440 900
```
in each Display subsection in xorg.conf

---

