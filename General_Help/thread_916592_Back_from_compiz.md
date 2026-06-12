---
title: "Back from compiz"
date: 2008-09-11
forum: General Help
---

### Post by Mickey Joe on 2008-09-11
Hello poeple of UbuntuForums.
 This is my first post, so i hope at the end it will be usefull...


 Few week`s back i installed compiz, and used for a while, till my nervs i could not take the laggy pc any more, so i tryed to take the compiz away from my pc. But i knew that i will remove it and later i will need it i will have some problems. So i opened the command line (alt+f2) and entered 
> gtk-window-decorator --replace
nothing happend :/
so i tryed to enter
> xfwm4
and my default window decorations came back. But! now i open Xfce menu and goto settings manager, select window manager and it says 
> These settings cannot work with your current window manager (unknown)
the same with Window manager tweaks

 so what should i do, to use gtk window manager ? :guitar:

 i use xubuntu 8.4

---

### Post by Mickey Joe on 2008-09-11
can somebeody actually please try to help me ? :)

---

### Post by victor.zamanian on 2008-09-11
Mmkay :-|

I'm not sure if I understand you correctly but isn't it possible to disable the window compositing just by:

Applications->Settings->Settings Manager->Window Manager Tweaks->Compositor->Enable display compositing ?

That's how I turned off the effects on my Xubuntu laptop.

---

### Post by Mickey Joe on 2008-09-11
theres the problem! - i cannot acces the window manager tweaks, it displays the error message

---

### Post by kokkus on 2008-09-11
So y dont u just disable compiz under visual effects then? 
Or u can use compiz-switcher to turn it on/off when u need to use compiz and not.

---

### Post by Trail on 2008-09-11
How about "metacity --replace &"

Which is the window manager instead of just the decorator.

Edit: Ah, you are using XFCE. Sorry, I read gtk and though of GNOME. I don't know how it's called.

---

