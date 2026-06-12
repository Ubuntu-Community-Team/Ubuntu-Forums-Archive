---
title: "Conflicting Shadows with Emerald"
date: 2008-08-11
forum: General Help
---

### Post by hung0702 on 2008-08-11
I installed the Compiz Fusion icon and chose Emerald as my windows decorator (as opposed to kwin). The windows look great, but if you check out the picture, the menu bar leaves a lot to be desired.

I don't necessarily want to change the system theme at this point in time, but I would like to fix the shadowing problem. If you look closely, there is also a transparent bar between the menu and the shadow. The same happens everytime I right-click (except without the bar), so I think it's just Kubuntu's window manager messing with me.

As a comparison, my screenshot also includes the shadow of GIMP windows, which appear fine.

I'd appreciate any help. I just switched from GNOME to KDE in hopes that I'd have more flexibility and could do what I wanted graphically.

---

### Post by rainwalker on 2008-08-12
I don't know about that extra border you have around your menus, but you can adjust the color, radius, and opacity of Emerald's shows in the Emerald theme manager; it's under the Edit Themes tab at the top

---

### Post by hung0702 on 2008-08-13
Um, ok.

I appreciate the reply, but it's the extra border and shadowing that are the problem. I've already played around with the settings and got the shadowing and blurring set how I want it.

I think this is the problem: The menu already has default shadowing, and Emerald is simply layering its shadows on top of the menu's. But Kwin is already disabled as the window decorator and manager. So what else do I need to disable in order to let Emerald do it's thing everywhere?

---

### Post by rainwalker on 2008-08-13
Hm...I haven't messed with Kwin much, so I'm not really sure what to tell you...

I'm sorry I couldn't be more helpful :(

---

### Post by Cheiron on 2008-08-15
Emerald's shadows leave a lot to be desired. 

For starters, on a window, it will draw a shadow for itself, but not for the window it wraps. This means that if a window has a very thin border, the shadow will be top-heavy. They seem to compensate for this in menus and other undecorated windows by shadowing for the whole thing, which causes much darker shadows.

Additionally, it doesn't seem to play well with KDE's built-in shadows. They end up drawing their shadows out past KDEs own, as it seems incapable of realising that KDE's shadow isn't just another part of the window.

---

### Post by oobuntoo on 2008-08-19
KDE's effects need to be disabled to get rid of extra (unwanted) shadow. From teminal or konsole, run kcontrol. Under "Appearane & Themes", select "Style". On the right hand-side, click on "Effects" tab and just disable everything.

---

