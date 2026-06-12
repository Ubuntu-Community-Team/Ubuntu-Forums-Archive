---
title: "Can't install new themes"
date: 2008-08-15
forum: General Help
---

### Post by Marty McFly on 2008-08-15
I found a few themes from gnome-look that i wanted to test drive, so I extracted the files and tried to copy to /usr/share/gdm/themes and it's saying permission denied and that I'm not root user.

My user is the only user to this operating system, how do I fix this?

---

### Post by karthikophobia on 2008-08-16
U are not the only user, there's another user called root.

open terminal and type
```
sudo nautilus
```
this will open up a window with root privileges. u can copy them now.

---

### Post by eggdeng on 2008-08-16
> I extracted the files
You don't need to do any of this. Just open Preferences->Appearance and drag and drop the tar.gz file onto it. Magic, new theme!

---

### Post by the yawner on 2008-08-16
Hold your horses. If you meant installing a GDM theme, just click under System>Administration>Login Window. It will open the Login Window Preferences. In the local tab there's an add button to install GDM themes.

---

