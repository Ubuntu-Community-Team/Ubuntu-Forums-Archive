---
title: "[SOLVED] exit, minimize, resize buttons stuck in OSX position"
date: 2008-09-11
forum: General Help
---

### Post by FalloutMan on 2008-09-11
So i tried the mac4lin theme verson 1.0 RC and liked it except that the buttons are all on the left side instead of the right.  After figuring out that emerald can fix that issue I attempted to revert back to the standard human theme but the buttons went back to the left side.  How can I make them go back to the right?  I like the basic human more so than the osx for simplicity reasons, so thats why I want to go back to the standard human theme.  Im on 8.04.1

SOLVED: So I emailed Infra Red Dude and he promptly replied with the following so im gunna post it just in case anyone wants to know:
> Yeah sure. Just open up a terminal window and execute this code:

 ```
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"
```

You could also do the same by launching the gconf-editor and going to the appropriate folder as indicated in the path above :)

---

