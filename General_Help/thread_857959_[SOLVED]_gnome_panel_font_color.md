---
title: "[SOLVED] gnome panel font color"
date: 2008-07-13
forum: General Help
---

### Post by vikramaditya on 2008-07-13
I've modified my gnome panels to a dark blue and would now like white fonts on it.  I've installed the gnome color chooser thingy, but it does not appear to support that function.  Also tried creating, modifying, & saving to my home folder a gtkrc-2.0 file, but nothing's changed.  does _anyone_ know an easy way to get white fonts to appear on the panels? :confused:

---

### Post by vikramaditya on 2008-07-16
*bump*...anyone?

---

### Post by mcduck on 2008-07-16
Did you name the fiel as "gtkrc-2.0" or ".gtkrc-2.0". The dot in the beginning is important.

Also, did you try logging out and back again after creating the file?

The following piece of code (in ~/.gtkrc-2.0) should definitely change the panel text color:
```
style "panel"
{
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
```

---

### Post by vikramaditya on 2008-07-17
Thanks, **mcduck** :)  I tried again with the .gtkrc-2.0 file, but the sonofawhore just won't work.  However, I finally found a tutorial (right here in the forums!) that shows how to do it using the gnome color chooser thingy.  The app would benefit from a less ambiguous menu, but everything's cool now.  Note the XP style panels . . . :)

[IMG]http://i205.photobucket.com/albums/bb264/Ginchiest/whitefonts.png[/IMG]

---

### Post by tlamer on 2009-08-25
hi... can you post the link here??? im not succesful googling it... please... thanx

---

