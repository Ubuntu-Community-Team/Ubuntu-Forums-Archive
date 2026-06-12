---
title: "Any way to lock quick launches from deletion?"
date: 2008-08-19
forum: General Help
---

### Post by zx6r1033 on 2008-08-19
There are some of my items on the panels that I keep deleting when I go to empty the trash or edit the menus. Is there any way to keep this from happening? I mean... aside from "stop being an idiot." lol. Can I lock them so they won't delete?

---

### Post by deanjm1963 on 2008-08-19
easy done.

hit Alt-F2 and type gconf-editor and hit enter

look for "Panels" - then "Global" (I think - using KDE at the moment) and check the box that says "Lock Panels"

hope this helps

---

### Post by zx6r1033 on 2008-08-19
It says the location could not be found.

---

### Post by deanjm1963 on 2008-08-19
when you open gconf-editor you see on the left hand side some entries with arrows, when clicked on make longer lists.

from memory, click on the first entry which will show up a whole list of programs, etc. scroll down to panels, then look under either global or general for "lockdown panels" or something similar.

---

### Post by zx6r1033 on 2008-08-19
> **deanjm1963 said:**
> when you open gconf-editor you see on the left hand side some entries with arrows, when clicked on make longer lists.

from memory, click on the first entry which will show up a whole list of programs, etc. scroll down to panels, then look under either global or general for "lockdown panels" or something similar.


It's the gconfig-editor that cannot be found.

---

### Post by deanjm1963 on 2008-08-19
it is " gconf-editor " not "gconfig-editor " .

---

### Post by zx6r1033 on 2008-08-19
> **deanjm1963 said:**
> it is " gconf-editor " not "gconfig-editor " .

:oops:  heh  I knew that. 


Thanks!

---

### Post by deanjm1963 on 2008-08-19
glad you found it ...

:)

---

