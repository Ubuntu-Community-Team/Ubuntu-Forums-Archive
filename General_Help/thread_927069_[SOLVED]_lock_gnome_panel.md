---
title: "[SOLVED] lock gnome panel"
date: 2008-09-22
forum: General Help
---

### Post by ktechman on 2008-09-22
Cheers everyone,

     Is there a patch that will create a lock dialog in the context menu of the gnome panel.  I have a user who keeps moving the top panel to the side and bottom.  I saw a patch in launchpad but there was no explanation of how it is supposed to be applied.  Any love out there today??

---

### Post by nowshining on 2008-09-22
a patch - u must download the source of the program ur trying to patch and apply the patch, and compile the program, there is a way to lock the panels, but i forgot the program, try looking in synaptic for something called lockdown, etc..

---

### Post by ktechman on 2008-09-22
Thank you.Perfect!!!!

---

### Post by seshomaru samma on 2010-02-19
the program is called " pessulus "
you can apt-get it

---

### Post by jalfrock on 2010-06-19
I installed pessulus and then got curious and started looking around in gconf-editor.  It turns out there's a setting for it, so pessulus probably just tweaks your gconf settings.  On the command line (i.e. in Terminal) type the following:

```
gconftool --set --type bool /apps/panel/global/locked_down true
```

---

