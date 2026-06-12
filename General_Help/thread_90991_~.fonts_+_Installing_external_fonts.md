---
title: "~/.fonts + Installing external fonts"
date: 2005-11-16
forum: General Help
---

### Post by mr.p on 2005-11-16
I have been trying all night to install a font I downloaded it is *.pcf in particular the popular ProFont.  I opened fonts:/// in Gnome and pasted the *.pcf files in there Gnome created /home/nathan/.fonts/* and put them all in there I have rebooted, etc. but I can't get the fonts to be selectable.  Any ideas how to get this to work or why the Gnome install method isn't working?

---

### Post by gapplewagen on 2005-11-16
Have you tried running:

you@you:~$ fc-cache

??

From the man pages:

       fc-cache scans the font directories  on  the  system  and  builds  font
       information  cache  files  for  applications using fontconfig for their
       font handling.

---

### Post by mr.p on 2005-11-16
Yes, I have still no luck... :(

---

### Post by oskude on 2005-11-16
i had yesterday my first peek to linux and bitmap-fonts and heres what i did

got a courier bdf font from here:
[http://cvs.freedesktop.org/xorg/xc/fonts/bdf/75dpi/courB10.bdf?view=log](http://cvs.freedesktop.org/xorg/xc/fonts/bdf/75dpi/courB10.bdf?view=log)

edited it a little with "fontforge" (allso changed the
fontname and family) and saved(created) it as bdf font.

converted it with "bdftopcf" and gzipped it.
(i gzipped it only cause /usr/share/X11/fonts/75dpi/* are gzipped too)

used (STEP4) instructions here:
[http://www.dgp.toronto.edu/~mjmcguff/learn/x11fonts/](http://www.dgp.toronto.edu/~mjmcguff/learn/x11fonts/)
(note, i added my "FontPath" manually to xorg.conf)

works!

"xfontsel" is a good prog to test if your bitmap-font is installed...

BUT!

i use my bitmap-font in a program called "puredata" and there it works, but i was unable to find my bitmap-font under gnome applications...

cheers
osku[de]

---

### Post by mr.p on 2005-11-16
Thanks for that.

I ended up downloading the *.ttf version working nice through X but I guess if I want it out of X I will need to setup the *.pcf version.

---

