---
title: "Compiz Opacity"
date: 2008-07-16
forum: General Help
---

### Post by quantum-positron on 2008-07-16
With Compiz's Opacity Settings only windows on top of the window the mouse are transparent. What I want is for the active window to be solid and all others transparent preferably with program exceptions I.e. I want mythtv or totem to stay solid as well. Is this possible with Compiz or another program?

---

### Post by DaymItzJack on 2008-07-16
> **quantum-positron said:**
> With Compiz's Opacity Settings only windows on top of the window the mouse are transparent. What I want is for the active window to be solid and all others transparent preferably with program exceptions I.e. I want mythtv or totem to stay solid as well. Is this possible with Compiz or another program?

This sounds like ADD helper. it's already a plugin in compiz, just adjust it so that transparency is higher and saturation is lower.

---

### Post by quantum-positron on 2008-07-16
Thanks that works much better. One more question. Is there any way to prevent mythtv from being transparent?

---

### Post by DaymItzJack on 2008-07-16
> **quantum-positron said:**
> Thanks that works much better. One more question. Is there any way to prevent mythtv from being transparent?

Go back to the ADD helper plugin and in the "Misc. Options" tab, do something like:

```
(Toolbar | Utility | Dialog | ModalDialog | Fullscreen | Normal) & !title=Buddy List
```

Of course, change Buddy List to whatever the mythtv's title is, or just use the "+" button on the right side and select "inverted" and "and" for the two options, along with the window class/title/etc.

---

### Post by quantum-positron on 2008-07-16
Thanks a bunch my desktop is now perfect :)

---

