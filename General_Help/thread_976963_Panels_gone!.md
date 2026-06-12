---
title: "Panels gone!"
date: 2008-11-09
forum: General Help
---

### Post by mschap on 2008-11-09
The top panel bar and bottom panel bars are gone.  I get the desktop window that is it.  Nothing for apps or even a log off button.  It is not that the icons are missing from the panel but the whole panel is gone.  This is weird -- worked fine last Friday.  Now it is gone.

Any solution involving the terminal is appreciated but I don't even know how to open a terminal as there is no menu access (well no menus either)

---

### Post by adult swim on 2008-11-09
hit alt+F2 and type in ```
gnome-panel
```

---

### Post by mschap on 2008-11-09
thanks but alt-F2 (function key 2) does not work

---

### Post by fooman on 2008-11-09
do you have an f-lock key on your keyboard? ...mine does and the "f" keys do not work unless i press that first.  if you do not have that,  or it doesn't work...you could give this a try:

press ctrl-alt-f1 to get to a virtual terminal...there will be no gui,  so write down the following command.  log in to the terminal session and type this:

```
sudo apt-get install nautilus-open-terminal
```

after it installs,  reboot with:

```
sudo reboot
```

when you get back to the desktop,  you can right-click anywhere on it and choose "open in terminal".  in the terminal type or copy/paste:

```
gnome-panel &
```

hope that works.

---

### Post by adult swim on 2008-11-09
alternatively you can right click the desktop, create a new document, paste in ```
#!/bin/bash
gnome-panel
``` then right click that file, go to properties>permissions and make it executable.  then double click it and run it

---

### Post by mschap on 2008-11-10
thanks it worked well.

---

### Post by Sjun on 2011-05-03
> **adult swim said:**
> alternatively you can right click the desktop, create a new document, paste in ```
#!/bin/bash
gnome-panel
``` then right click that file, go to properties>permissions and make it executable.  then double click it and run it

Had the same problem after I set "User defined session" for the login screen.
The above solution worked like a charm and so I was able to restore the default settings.

\\:D/

---

