---
title: "nVidia driver overscan and giant fonts"
date: 2011-03-25
forum: Hardware
---

### Post by emunson on 2011-03-25
I just installed a G 210 into my HTPC and started using the proprietary drivers and I am having some issues with the display.  MythTV is happy and when I watch movies/recordings that have black bars above and below the picture I don't really notice, but on full screen videos or at the desktop there are definitely pixels missing.  A search turned up a slider that is supposed to be in the nvidia-settings program, but this option is not present for me, at least that I can see.  Which leads into problem 2, since the switch to the binary driver the font size used is giant.  On a 37" 1080p tv the letters are 1/2 inch tall in every menu which is making for problems with windows that are too big to fit on the desktop and they won't let me shrink them (like nvidia-settings).

Here is a pic to demonstrate the large fonts:
[ATTACH]187092[/ATTACH]

---

### Post by emunson on 2011-03-29
I solved this by setting the DPI in my xorg.conf, the calculated value must have been incorrect.

---

### Post by ivanmara on 2012-01-23
also you can create file in home folder:

touch ~/.Xresources

and add this lines:

Xft.dpi: 96
Xft.antialias: true
Xft.rgba: rgb
Xft.hinting: true
Xft.hintstyle: hintslight

after relogin new dpi will aplly

---

