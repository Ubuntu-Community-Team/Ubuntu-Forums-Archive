---
title: "Panel position reversed every time login."
date: 2008-10-02
forum: General Help
---

### Post by Masterart on 2008-10-02
Ubuntu hardy ,  every time I login the panel with orientation "top" is at bottom and that with orientation "bottom" is at top ?

---

### Post by drs305 on 2008-10-02
Here is something to check. Open gconf-editor:
```
gconf-editor
```

Drill down to /apps/panel/toplevels
Look at "bottom_panel_screen0  and make sure "orientation" says bottom.
Look at "top_panel_screen0" and make sure "orientation" says top.

---

