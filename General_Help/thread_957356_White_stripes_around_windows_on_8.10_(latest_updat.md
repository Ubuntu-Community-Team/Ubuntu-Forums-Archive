---
title: "White stripes around windows on 8.10 (latest updates applied)"
date: 2008-10-24
forum: General Help
---

### Post by matn1 on 2008-10-24
Folks,

I've searched for the source of this problem to no avail...

Whenever I suspend and resume, almost all of the windows on my desktop (Nautilus, Rhythmbox are exceptions to the rule) have a white contour. Even application menus appear with a  white contour (about 2 mm wide) which masks a portion of the content of the window/menu in question.

Disabling, and re-enabling "Window Decorations" in compiz (through the compiz settings manager) solves the issue. Its quite annoying though as I do use the suspend functions much on my laptop. I don't really want to disable compiz.

Anyone has any idea how to solve this?

---

### Post by matn1 on 2008-10-24
UPDATE:

```

root@sin:/etc/acpi/resume.d# cat 99-window-decorator.sh 

#!/bin/sh

/usr/bin/compiz-decorator --replace

```

Seemed to solve it. Not sure why this isn't already handled somehow as it was in 8.04.

---

