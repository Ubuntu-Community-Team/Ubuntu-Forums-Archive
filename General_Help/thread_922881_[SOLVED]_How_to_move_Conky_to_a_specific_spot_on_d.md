---
title: "[SOLVED] How to move Conky to a specific spot on desktop?"
date: 2008-09-17
forum: General Help
---

### Post by xj0hnx on 2008-09-17
Hi :)

I have Conky up and running but I have an issue with it. When I download something to my desktop it seems to always get put under Conky, so I have to $ killall conky to stop it, so I can move it. I am using dual monitors with twinview so both monitors form one large screen. I want Conky on the left monitor, but on the right side, right now it is on the left. Is there a way to move it to the right side? When I tried Alignment center, it just moved it to the left side of the left monitor :(

---

### Post by Locutus_of_Borg on 2008-09-17
# position
alignment top_right
gap_x 0
gap_y 0


increase from 0 in each line to move further away from whichever corner is specified in alignment

---

### Post by cardinals_fan on 2008-09-17
Add ${voffset *} and ${offset *} to change the vertical and horizontal position, respectively.

---

### Post by xj0hnx on 2008-09-17
> **Locutus_of_Borg said:**
> # position
alignment top_right
gap_x 0
gap_y 0


increase from 0 in each line to move further away from whichever corner is specified in alignment

Thanks you, worked perfect :)

---

### Post by Locutus_of_Borg on 2008-09-17
you can put in:

own_window_hints below


to keep it from ever being on top of other applications as well

---

### Post by xj0hnx on 2008-09-17
> **Locutus_of_Borg said:**
> you can put in:

own_window_hints below


to keep it from ever being on top of other applications as well

It already has this in that line...

```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

Is there somewhere that explains what all the commands mean, and a list of colors it can use?

---

