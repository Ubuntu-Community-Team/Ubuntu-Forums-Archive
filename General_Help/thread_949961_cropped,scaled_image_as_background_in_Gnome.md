---
title: "cropped,scaled image as background in Gnome"
date: 2008-10-16
forum: General Help
---

### Post by tuesdave on 2008-10-16
I'm using Gnome/Compiz and need a way to set a background image besides Gnome's standard background-setting dialog.  I don't know how many people are still familiar with John Bradley's XV, but I've been using a command like this for years:

[INDENT]```
xv -quit -root -crop 2335 0 2335 1868 bigimage.jpg
```[/INDENT]

This crops a large image and scales it to fit on the root window.  It appears that xsetbg/xloadimage can do the same kind of thing.

The problem is that in Gnome, the "Desktop" window is not the same as the root window and these command-line utilities do not work.  Nor can I successuflly specify the Desktop window id as an argument for any of the above mentioned utilities.

Is there any way to accomplish this task in Gnome?

Thanks in advance,
Dave Riesz

---

