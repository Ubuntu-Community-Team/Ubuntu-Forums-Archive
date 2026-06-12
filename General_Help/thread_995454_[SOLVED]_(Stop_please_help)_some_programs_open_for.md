---
title: "[SOLVED] (Stop please help) some programs open for 0.5 se and close  after using  syn"
date: 2008-11-27
forum: General Help
---

### Post by Hyper Tails on 2008-11-27
Hi I run Intrepid ibex ands I have a BIG!!! issue going on with my desktop
that is I was using the synapic package manager to install some addtional stuff and after i did it Some programs won't open like
i)simple compiz configure
ii) my dock configureation
iii)my klamtk anti-virus opens and scans but when i'm scaning the entire system it eventually freezes the system
iv) in some programs like fire fox and klam my cursor turns black when I don't want it to!
v) I want to edit my animations in compiz I can't because when I click on it it closes

please help I really really REALLY! need help with this

---

### Post by Hyper Tails on 2008-11-28
anyone?

---

### Post by Hyper Tails on 2008-11-28
......................................................................................................

---

### Post by Hyper Tails on 2008-11-29
:confused:Please:confused:

---

### Post by oldos2er on 2008-11-29
What "additional stuff" did you install?

---

### Post by Hyper Tails on 2008-11-29
compiz-extra plugins
clam av and random stuff

sorry I honestly forgot what i installed

---

### Post by bobbob1016 on 2008-11-29
Try running those programs from the terminal, as in run ccsm for compiz config settigs manager, or kiba or whatever, and paste the results here.  It'll help get a diagnosis.

---

### Post by Hyper Tails on 2008-11-29
compiz config manager
```
liam@liam-desktop:~$ ccsm
/home/liam/.themes/BlackWinter/gtk-2.0/panel.rc:13: Unable to locate image file in pixmap_path: "shadows/window-bg.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:179: Unable to locate image file in pixmap_path: "/shadows/shadow-in.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:182: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:189: Unable to locate image file in pixmap_path: "/shadows/shadow-in.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:192: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:199: Unable to locate image file in pixmap_path: "/shadows/frame1.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:202: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:209: Unable to locate image file in pixmap_path: "/shadows/shadow-none.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:212: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:218: Unable to locate image file in pixmap_path: "/shadows/frame1.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:221: Unable to locate image file in pixmap_path: "/shadows/shadow-none.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:223: Unable to locate image file in pixmap_path: "/shadows/shadow-none.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:227: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:1060: Unable to locate image file in pixmap_path: "/menu/menu.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:1063: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:1100: Unable to locate image file in pixmap_path: "/menu/menuitem.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:1103: Background image options specified without filename
Segmentation fault
liam@liam-desktop:~$ 

```

---

### Post by Hyper Tails on 2008-11-30
halllllo? anyone?

---

### Post by oldos2er on 2008-11-30
You could try running "metacity --replace" in a terminal to see if it helps with getting apps to run. This will turn off the 3d eye candy though.

---

### Post by Hyper Tails on 2008-11-30
```
liam@liam-desktop:~$ metacity --replace
/home/liam/.themes/BlackWinter/gtk-2.0/panel.rc:13: Unable to locate image file in pixmap_path: "shadows/window-bg.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:179: Unable to locate image file in pixmap_path: "/shadows/shadow-in.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:182: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:189: Unable to locate image file in pixmap_path: "/shadows/shadow-in.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:192: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:199: Unable to locate image file in pixmap_path: "/shadows/frame1.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:202: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:209: Unable to locate image file in pixmap_path: "/shadows/shadow-none.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:212: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:218: Unable to locate image file in pixmap_path: "/shadows/frame1.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:221: Unable to locate image file in pixmap_path: "/shadows/shadow-none.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:223: Unable to locate image file in pixmap_path: "/shadows/shadow-none.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:227: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:1060: Unable to locate image file in pixmap_path: "/menu/menu.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:1063: Background image options specified without filename
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:1100: Unable to locate image file in pixmap_path: "/menu/menuitem.png"
/home/liam/.themes/BlackWinter/gtk-2.0/gtkrc:1103: Background image options specified without filename
liam@liam-desktop:~$ 

```

---

### Post by oldos2er on 2008-11-30
Since your "BlackWinter" theme seems to be broken, try a different one.

---

### Post by Hyper Tails on 2008-11-30
i reinstalled ubuntu
that worked

---

### Post by oldos2er on 2008-12-01
> **Hyper Tails said:**
> i reinstalled ubuntu
that worked

 Ouch! Just as long as you understand that was unnecessary--it's like swatting a fly with an H-bomb.

---

### Post by Hyper Tails on 2008-12-01
Sorry

> it's like swatting a fly with an H-bomb. 
LOLOLOLOL

---

