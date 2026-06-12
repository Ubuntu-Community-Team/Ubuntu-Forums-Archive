---
title: "startx permissions"
date: 2008-08-07
forum: General Help
---

### Post by weweboom on 2008-08-07
I screwed up my login so I have to use startx to fix it, I need to access system administration  login window to fix it, but I get this message:'
```
GDM (GNOME Display Manager) is not running
you might be using a different display manager, such as KDM, CDE, or xdm, if you wish to use this feature, then your system will need to be configured to use GDM instead
```what can I do to access login window

---

### Post by iaculallad on 2008-08-07
On the terminal:

```
sudo nano -B /etc/X11/default-display-manager
```

Change whatever line the file contains with **/usr/sbin/gdm**. Save and Close. And on your terminal again, input the command below:

```
sudo /etc/init.d/gdm
```

---

### Post by weweboom on 2008-08-07
It didn't work GDM was already set as the manager, it works fine when not in startx mode just like this, isn't there a system restore option or something?

---

### Post by loboc on 2008-08-07
nano ~/.xsession and see if gdm is listed in there startx shouldn't start gdm

sudo dpkg-reconfigure gdm is a easier way to pick a login manager

and sudo /etc/init.d/gdm restart is a more practical way to start or restart gdm

---

