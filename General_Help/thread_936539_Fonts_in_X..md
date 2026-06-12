---
title: "Fonts in X."
date: 2008-10-02
forum: General Help
---

### Post by webfrage on 2008-10-02
Hello,

I have recently installed the command-line version of Ubuntu Hardy Heron.  I subsequently installed the X Window System.  I am trying to change the font for xterm.  I want to use one of the fonts in /usr/share/fonts/truetype/ttf-dejavu.  However, I cannot see these fonts with xfontsel. I also cannot see the font with xlsfonts.  This problems persists even if I use the command ttmkfdir to construct a list of the fonts.  The Font Path also does not appear when I check it with the command 'xset q.'

I tried to edit the file /etc/X11/xorg.conf directly, by adding the paths to the fonts, but this did not work.  My impression is that the fonts' paths are built when X starts up.  Can anybody tell me what to do about this?

A second related question is this:  if I type

xterm -fa Mono -fs 10

then I get a satisfactory font;  how do I add this to the file ~/.Xresources, so that it is loaded automatically?  I do not want to use an alias, as I want it to be in effect even if I don't start the xterm from the command line.

Thanks!

---

