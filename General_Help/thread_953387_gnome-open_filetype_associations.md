---
title: "gnome-open filetype associations"
date: 2008-10-20
forum: General Help
---

### Post by Stefanie on 2008-10-20
I have a problem opening .tex files. I have set gvim as the default "open with" application in nautilus, but when i run "gnome-open ~/file.tex" in a terminal I get the error

```
Error showing url: There is no default action associated with this location.
```

Because of this, opening a .tex file with gnome-do does not work either and this is really annoying. double-clicking a file in nautilus works fine, though. 

I  have tried editing /etc/gnome/defaults.list (added a line "text/x-tex=gvim.desktop", but that didn't work.

---

### Post by northern lights on 2008-10-20
I'm sure this can be solved more elegantly via setting the default app such that *gnome-open* will make use of it, however, why would you not simply run```
gvim ~/file.tex
```

---

### Post by Stefanie on 2008-10-20
> **northern lights said:**
> I'm sure this can be solved more elegantly via setting the default app such that *gnome-open* will make use of it, however, why would you not simply run```
gvim ~/file.tex
```

read my post again, i know that i can open my tex files that way, but the problem is that gnome-do uses xdg-open (both xdg-open and gnome-open return the same error message) so i can't use gnome-do with tex files.

---

