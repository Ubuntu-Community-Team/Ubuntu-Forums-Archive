---
title: "[SOLVED] Gdm"
date: 2008-09-02
forum: General Help
---

### Post by Uchiha_madara on 2008-09-02
Hi every one ,

I installed KGet Download manager and i have changed the gdm to
kdm of KDE - ithink - I need to return using GDM of Gnome again how ?????

---

### Post by Zorael on 2008-09-02
```
$ sudo dpkg-reconfigure gdm
```
Also when in the login window (upon next logging in) make sure to set Session to gnome.

---

### Post by Uchiha_madara on 2008-09-02
> **Zorael said:**
> ```
$ sudo dpkg-reconfigure gdm
```
Also when in the login window (upon next logging in) make sure to set Session to gnome.



the terminal give me this error message :
>  
* Reloading GNOME Display Manager configuration...                             
* Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.


---

### Post by WRDN on 2008-09-02
Press Ctrl, Alt and Backspace to restart X.

---

### Post by Uchiha_madara on 2008-09-05
thanks it works ...

---

