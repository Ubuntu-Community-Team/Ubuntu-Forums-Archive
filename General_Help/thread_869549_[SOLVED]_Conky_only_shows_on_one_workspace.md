---
title: "[SOLVED] Conky only shows on one workspace"
date: 2008-07-24
forum: General Help
---

### Post by Patricrawley on 2008-07-24
I have conky in my startup sessions, but it only shows on one workspace. I have to kill the process and restart it to get it to show on all workspaces. Does anyone know how to fix this issue?

---

### Post by tamoneya on 2008-07-24
how are you starting it up.  Are you using something like:```
conky -c ~/.conkyrc
```
or are you using a separate script.

---

### Post by Patricrawley on 2008-07-24
Yeah, it's using the conkyrc script in my home folder.

---

### Post by tamoneya on 2008-07-24
that can cause some confusion with gnome when it loads.  I do it with a script and I launch this script instead of just calling the conky command.

contents of ~/.conkystartup:```
#!/bin/bash
sleep 30 &&
conky -c ~/.conkyrc;
```
Basically it waits 30 seconds before starting conky.  This lets gnome get ready before you start conky.

---

### Post by Patricrawley on 2008-07-25
Thanks, that did the trick

---

