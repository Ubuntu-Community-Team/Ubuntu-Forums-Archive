---
title: "Cairo Dock wont work"
date: 2008-08-27
forum: General Help
---

### Post by Orlsend on 2008-08-27
Hi

I removed AWN because I herd Cairo was better, I tried to install it 2 times and it seems the same

```
paez@paez-laptop:~$ cairo-dock
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
Unable to locate theme engine in module_path: "aurora",
Unable to locate theme engine in module_path: "aurora",
Unable to locate theme engine in module_path: "aurora",
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:120)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:120)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:120)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
new backing pixmap (bis) : 79691782
window pixmap : 1023x693
window pixmap : 1023x693
new backing pixmap (bis) : 79691784
window pixmap : 1023x693
window pixmap : 1023x693

```

Any help would be great

---

### Post by Orlsend on 2008-08-28
*Bump*

C'mon guys

---

### Post by fabounet on 2008-08-28
are you sure it's not running and hiding somewhere behind your gnome-panel for exemple ?
try a ```
ps -ef | grep cairo
```

also, "cairo-dock -l debug" can give some useful info.
which version are you using ?

---

### Post by Orlsend on 2008-08-28
Latest... it keep working in the backgruound hogging my RAM

---

### Post by Crafty Kisses on 2008-08-28
Post the results of > top

---

### Post by Orlsend on 2008-08-28
> paez      8738  8581  2 11:51 pts/0    00:00:00 cairo-dock
paez      8827  8772  0 11:52 pts/1    00:00:00 grep cairo

that was the out put

---

### Post by RiMkA on 2008-09-16
> **Orlsend said:**
> Latest... it keep working in the backgruound hogging my RAM

I had similar problem. 

1. Make sure that no instance of cairo-dock is running. Turn them off via System Monitor.
2. Go to Places > Home Folder > .cairo-dock
3. Delete 'current_theme' folder

That worked for me. Give it a try. :guitar:

---

