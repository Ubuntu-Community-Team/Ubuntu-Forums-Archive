---
title: "Problems when opening cairo-dock for the first time."
date: 2008-09-03
forum: General Help
---

### Post by RosieKins on 2008-09-03
I'm not new to ubuntu, but I've decided to get adventurous and customise my desktop. 
I decided to install cairo-dock and I followed ```
https://help.ubuntu.com/community/CairoDock#From%20the%20repository%20(stable)
``` and everything seemed to install fine. 

So I go to start it up in terminal....

```
angel@jazz:~$ cairo-dock
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:120)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/home/angel/.cairo-dock/current_theme/launchers/trash_empty.png': No such file or directory
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/home/angel/.cairo-dock/current_theme/launchers/trash_full.png': No such file or directory
warning :  (applet-init.c:_load_theme:72)  
  Attention : couldn't find images, this theme is not valid
```

This is what I got..... :(  Cairo-dock started up - but.... It has this horrible black background and I can't seem to get rid of it.  
I'm using Hardy if this is anyhelp. 

Any help would be appriciated. 

RosieKins

---

### Post by billgoldberg on 2008-09-03
I installed cairo from the .deb files here (the main and plugin ones) and they work fine.

Are you running compiz fusion? You should for cairo dock to properly function.

---

### Post by RosieKins on 2008-09-04
I am using Compiz Fusion.....:/

Could they not be working together?

---

