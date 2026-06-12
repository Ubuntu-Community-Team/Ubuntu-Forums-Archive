---
title: "ceaping our computers clean and tidy"
date: 2008-09-25
forum: General Help
---

### Post by nlz on 2008-09-25
Hello All,

We've got a community radio stations which runs completely on Ubuntu. We've got some problems keeping the computers working without too much maintenance. Some questions/issues which should be automated:

1.
We've got auto-login enabled so that people don't need to have a login or need to know a password. But now every time toolbars get lost. What command can we run at boot to let both toolbars be present and in the right position (with our own icons (audacity, audacious, soundkonverter, firefox, pidgin and nautilus in it), so ```
gconftool -2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation "top"
```
is not enough.

2.
It happens quite a lot that the file in /home/user/desktop are not displayed on the desktop. What can we do about this?

Thanks

nlz

---

