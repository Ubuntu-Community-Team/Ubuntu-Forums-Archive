---
title: "Compiz - disable decoration transparency on incative windows?"
date: 2008-07-19
forum: General Help
---

### Post by lxevolution on 2008-07-19
I've searched everywhere and I can't seem to find the answer. Is there any way to disable transparent window decorations on inactive windows using compiz (compiz-decorator, not emerald)? Screenshot of what I'm talking about is attached. All solutions are welcome - even compiling from source.

---

### Post by Slim Backwater on 2008-08-12
From 
[http://tombuntu.com/index.php/2007/10/04/adjust-the-transparency-of-window-decorations-with-compiz/](http://tombuntu.com/index.php/2007/10/04/adjust-the-transparency-of-window-decorations-with-compiz/)

Open the GNOME Configuration Editor by pressing Alt-F2 to open the Run Application dialog, and type gconf-editor and click Run.

Navigate to apps/gwd in the GNOME Configuration Editor. These are the two values you need to change:

    metacity_theme_active_opacity - (Transparently on active window’s title.)
    metacity_theme_opacity - (Transparently on inactive windows’ titles.) 

The value you can set is a decimal number, 1 is no transparently, and 0 is invisible.

HTH,

HAND

---

### Post by antario91 on 2008-10-18
Thank you for this answer, it annoyed me pretty much as well.

---

### Post by MobiusCoffee on 2009-04-08
Bump, I was trying to figure this out all day!

---

### Post by nortexoid on 2009-10-29
Nice. First google hit for me.

---

### Post by Gavin Wheeldon on 2011-03-02
Read this post JUST as i figured out how to do it:

Right, so you have used compizconfig settings to make translucent windows, yes? I'm guessing you have used "type=normal" and a window value. click this and edit it. then click the little 'add' button, select "window name" from the brop down box, and use 'grab' and select the vlc media player (OPEN VLC MEDIA PLAYER FIRST obviously. Then click 'invert' then 'add'.

Hope this works for you!!

WRONG POST SORRY!!! this technique might work in your situation though.... you could change the parameters.

---

