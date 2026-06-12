---
title: "Dual display increases CPU charge to 100%"
date: 2016-01-09
forum: Hardware
---

### Post by GSKishi on 2016-01-09
Hi all,

as a beginner, I have installed an Ubuntu Gnome 15.10 on an old laptop.
When I am using it, I get :
- this charge for CPU :
[ATTACH=CONFIG]266639[/ATTACH]
- processes charges as followed
[ATTACH=CONFIG]266640[/ATTACH]
which look normal

But when I plug an additional screen (HPLE19' btw) on VGA plug, for Dual Display usage 
- CPU charge becomes : 
[ATTACH=CONFIG]266638[/ATTACH]
- gnome-shell uses around 49% of CPU :-(
- but second screen displays normal wallpaper (no display issue)
- everything becomes obviously slow (i.e. moving a window, switching to another one, etc)

Answer of "sudo lshw -C video" is :

```
-NC10:~$ sudo lshw -C video
  *-display:0             
       description: VGA compatible controller
       produit: Mobile 945GSE Express Integrated Graphics Controller
       fabriquant: Intel Corporation
       identifiant matériel: 2
       information bus: pci@0000:00:02.0
       version: 03
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       ressources: irq:16 mémoire:f0000000-f007ffff portE/S:1800(taille=8) mémoire:d0000000-dfffffff mémoire:f0300000-f033ffff
  *-display:1 NON-RÉCLAMÉ
       description: Display controller
       produit: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       fabriquant: Intel Corporation
       identifiant matériel: 2.1
       information bus: pci@0000:00:02.1
       version: 03
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: pm bus_master cap_list
       configuration: latency=0
       ressources: mémoire:f0080000-f00fffff
```

Did I posted all needed information to solve this ?

Many thanks in advance

---

### Post by GSKishi on 2016-01-11
Please help, because I did not found any answer through my research on the web :-(

---

