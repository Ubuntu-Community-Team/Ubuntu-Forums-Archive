---
title: "Screenshots in fluxbox"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by DoorGunner on 2006-01-02
I know that in gnome and kde screenshots can be take with their handy applets. However, how can a screenshot be taken if you use Fluxbox??

---

### Post by ardchoille on 2006-01-02
You can take screenshots either from a terminal or creating fluxmenu items for the following commands.

**For immediate screenshots:**
```

import -frame screenshot.jpeg

```
This command will produce a cross-hair cursor. You can click on a window for a screenshot of that window, or you can click on the desktop for a full screenshot.


**For delayed screenshots:**
```

import -pause 10 -window root screenshot.jpeg

```
This command will take a full screenshot after a pause of 10 seconds. This is good if you want to include the fluxbox menu in the screenshot. This is what I used when creating screenshots of fluxbox styles that I used to make.

Either way, the screenshots will appear in your home directory by default. You can change the location by adding a path to the "screenshot.jpeg" (e.g. /home/user/documents/screenshot.jpeg).

---

### Post by DoorGunner on 2006-01-02
thank you ..... :D

---

### Post by zetsumei on 2006-12-22
i typed import -frame screenshot.png and it said command not found

---

### Post by taurus on 2006-12-22
I think import is part of the imagemagick package...

```
sudo aptitude update
sudo aptitutude install imagemagick
```

---

### Post by coolglobal on 2008-06-21
What a helpful thread, thank you everyone!

---

