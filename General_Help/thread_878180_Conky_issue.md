---
title: "Conky issue"
date: 2008-08-02
forum: General Help
---

### Post by Rask on 2008-08-02
Hey guys, I'm having some trouble setting up Conky properly.

I have it where I want it, and it works, but I can't get it to behave right. 

This is the config for the window:

```
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

When own_window_type is set to desktop, it stays open on my desktop and works, but when I do something on the desktop (touch an icon, drag the select box) it disappears. If I set own_window_type to root, it stays on my desktop and works until I hit the "show desktop" button, then it disappears. If I set it to override, it hovers ontop of all my windows and is extremely annoying.

Any ideas?

Thanks in advance.

---

### Post by spupy on 2008-08-02
Try to remove the "below" hint and see what happens. This is my setup:
```
own_window true
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,sticky,skip_taskbar,skip_pager
```

---

### Post by Rask on 2008-08-02
Thanks. I removed bottom and played around with it and now it works.

Ended up going with this if anyone is wondering:

```
own_window true
own_window_type override
own_window_transparent yes
own_window_hints undecorated,sticky,skip_taskbar,skip_pager
```

Thanks again!

---

