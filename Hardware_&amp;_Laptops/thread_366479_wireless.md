---
title: "wireless"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by mr.farenheit on 2007-02-20
i have one of those generic linksys pcmcia wireless g cards for my notebook. i'm just wondering as to if the kwifi feature will support the card and have it function correctly. i'm not big on wireless but i'd like to have it just in case and i'd like to find the easiest way to set it up.

---

### Post by featherking on 2007-02-20
with your card inserted and powered on try running in a terminal:
```
lspci
```

If you see a line somewhere that says something like 'linksys pcmcia' or something along those lines identifying your pc-card then the driver is loaded and it should work

---

### Post by mr.farenheit on 2007-02-20
awesome, worked like a charm. thx:)

---

### Post by featherking on 2007-02-20
np :)

---

