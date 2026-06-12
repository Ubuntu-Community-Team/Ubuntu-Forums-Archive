---
title: "Scalling titlewindow and panels"
date: 2008-09-27
forum: General Help
---

### Post by beun on 2008-09-27
Ive been trying to scale my titlewindows and panels, not really looking for extra applications or fancy customization options. Just scale them down to 21 pixels.

I actually managed to resize them to 21 pixels at one point but failed to notice how i did it. Think it had something to do with removing buttons from the panels but not sure, it seems to be locked at 24 pixels right now.

Does anyone know a solution for this?   


Thanks

---

### Post by gossrock on 2008-09-27
previously I recall being able to size the panals to 21 as well, but that was a long time a go on a previous version of Ubuntu. I have poked around and this is what I have experianced.

1) right click on the panal and select properties
     minumum size seems to be 23 pixles for me

2) open gconf-editor (<f2> gconf-editor)
     on the tree on the left go to:
          apps > panel > toplevels
               you can set the size property to 21
               unfortunately it seem to not actually change to be smaller.

Unfortunatly I am not any help.

---

### Post by beun on 2008-09-28
Thanks for your reply gossrock

seem to get a bit further, the option window you talked about explanes what causes the minimum size:

"The panel will set a minimum size based on the letter type size and other factors."

Now if we just know what other factors

---

### Post by beun on 2008-09-28
Found out this is a well known issue and allot of people are trying to tackle this minimum panel size, they have reported it as an bug. Confirmed at the following links:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/223075](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/223075)
[http://bugzilla.gnome.org/show_bug.cgi?id=537661](http://bugzilla.gnome.org/show_bug.cgi?id=537661)

---

### Post by gossrock on 2008-09-28
Interesting, thanks for the update.

---

