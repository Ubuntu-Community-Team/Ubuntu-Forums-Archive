---
title: "X Restarting itself"
date: 2005-11-27
forum: General Help
---

### Post by Internet on 2005-11-27
I've started get a problem with X just randomly restarting for no reason. A few days ago it would restart and bring me to GDM whenever I would open a program. Restarting my computer fixed it but it still happens sometimes. I left my computer on last night and came back to find it at the GDM login screen again. I think it might be my nvidia card drivers.. things like this happened when I had them installed previously. Does anyone know what my problem could be? And also, is there a way to go back to the default nvidia drivers?

---

### Post by taurus on 2005-11-27
I assume you mean the generic nv driver that comes with Xorg then!  You just have to edit your /etc/X11/xorg.conf and change the driver from nvidia to nv,

sudo gedit /etc/X11/xorg.conf

Scroll down until you see this line

Driver      "nvidia"

and replace it with

Driver      "nv"

---

### Post by Internet on 2005-11-27
Thanks, I changed it back to the generic driver. I hope this will solve my problem.

---

