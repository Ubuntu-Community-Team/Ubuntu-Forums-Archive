---
title: "resolution difficulties"
date: 2008-07-10
forum: General Help
---

### Post by mukeliller on 2008-07-10
I am unable to change my screen resolution. When attempting to through the System>Preferences>Screen resolution Path I receive this error: 

> The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

Is this indicative of a larger issue? Is there another way to change the resolution?

---

### Post by sayakb on 2008-07-10
At a terminal, do:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And then restart X (Ctrl+Alt+Backspace)

---

