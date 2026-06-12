---
title: "[SOLVED] conky keeps starting always on top"
date: 2008-10-10
forum: General Help
---

### Post by amrlima on 2008-10-10
I know there are a number of posts about conky around and this particular problem is also discussed, but I can't find any solution. My conky starts alwas on top off all windows. This is part of my conkyrc:

own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type override

I know setting to "own_window_type desktop" will make the issue disappear but that way wen I click on the desktop conky will vanish.

Anyone has a miraculous solution?

---

### Post by cammin on 2008-10-10
change
own_window_type override
to
own_window_type normal

---

### Post by amrlima on 2008-10-10
Yes, that helps! but one last annoying thing: clicking on the "show desktop" icon which I like to use to see conky.. but oh well one can't have everything..

---

### Post by Cresho on 2008-10-10
I use sessions to launch conky from a script.

#!/bin/bash
sleep 20 && conky;

it is delayed 20 seconds and its fine.  Never have problems.

---

### Post by amrlima on 2008-10-10
> **Cresho said:**
> I use sessions to launch conky from a script.

#!/bin/bash
sleep 20 && conky;

it is delayed 20 seconds and its fine.  Never have problems.

Thanks! That works great! should have thought of that :P

---

