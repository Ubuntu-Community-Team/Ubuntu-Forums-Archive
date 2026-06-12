---
title: "Cannot remove Cairo-Dock new launcher"
date: 2008-09-27
forum: General Help
---

### Post by redjam on 2008-09-27
Hello all,

I had tried to add a new manual launcher but must have cancelled or something.

Now I've been left with a separator icon with the label "New Launcher". When I right-click to delete it, there is only the Cario-Dock options menu, no modify or delete buttons.

Would really like to get rid of it - any ideas how?

Thanks in advance :)

---

### Post by fabounet on 2008-09-29
just go into the ~/.cairo-dock/current_theme/launchers folder, and search for a .desktop file that doesn't have any command

```
grep "Exec=$" *.desktop
```
 or something approaching
and delete this file.

---

### Post by jaret on 2008-11-07
Thanks, it helped me too.

---

