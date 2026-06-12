---
title: "Custom Terminal Size and Placement Upon X Startup"
date: 2008-07-18
forum: General Help
---

### Post by ferrellw on 2008-07-18
Is there anyway to have a custom size set and placement so that when X starts, the windows are where they are suppose to be instead all on top each other? I went into sessions and added the 3 terminal windows i wanted open with ```
gnome-terminal --working-directory=%f --geometry=88==**x**
``` but once the windows open they all open on top of each other.


Thanks,
Wesley

---

### Post by DaymItzJack on 2008-07-18
I don't know much about the geometry command but have you tried something similar to:

```
gnome-terminal --working-directory=%f --geometry=88==**x**
gnome-terminal --working-directory=%f --geometry=388==**x**
gnome-terminal --working-directory=%f --geometry=788==**x**
```

Or.. whatever?

---

### Post by ferrellw on 2008-07-19
I guess i should have consulted google before i posted here, but i found this awesome link that definitely deserves a looking at.

[http://multignometerm.sourceforge.net/web/doc/options.html]("http://multignometerm.sourceforge.net/web/doc/options.html")

Thanks
Wesley

---

