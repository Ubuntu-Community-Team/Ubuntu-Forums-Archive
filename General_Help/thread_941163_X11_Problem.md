---
title: "X11 Problem"
date: 2008-10-07
forum: General Help
---

### Post by dalewhitaker on 2008-10-07
Hi,

I've just downloaded Google Earth and have tried to unpack it.  I get the message:

"You don't seem to be running an X server (no DISPLAY set).
Google Earth and its installer both require X11."

Any ideas as to what I should install or select?

Many thanks in advance.

---

### Post by iaculallad on 2008-10-07
Try setting the display environment:

```
export DISPLAY=":0.0"
```

---

