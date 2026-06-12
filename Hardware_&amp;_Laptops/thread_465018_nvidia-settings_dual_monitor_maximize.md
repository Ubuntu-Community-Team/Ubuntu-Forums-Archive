---
title: "nvidia-settings dual monitor maximize"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by belaflek on 2007-06-05
So, I'm a 10 year windows guy and have been tinkering with Linux on and off for a few years and decided to take the pseudo plunge into Linux using ubuntu. I have a Dell D820 nVidia Quadro 512MB card and have Feisty installed. When I set the display to twin view, is there a way, when I maximize a window that it does not span both monitors or do I have to have a separate X on each screen?

---

### Post by spvo on 2007-06-11
I'm using twin view, and when I maximize a window/application it only takes up the screen that it resides on.  If I want it to take up both windows, I have to manually stretch it over both.

---

### Post by ArtificialSynapse on 2007-06-15
Okay now I have the opposite problem, I WANT it to only span in the screen that I'm working in rather than the entire span of both monitors; anyone know how to do that?

---

### Post by JLKenyon on 2008-06-19
Not sure if this helps, but I had the same problem initially.  I setup my screen with nvidia-settings so that both of my monitors were absolute coordinates, and applied it.  At that point, if I maximized a window, it would span both monitors.

However, when I saved the changes to my xorg file, logged out and logged back in, it behaved "normally" when I got back into Gnome.  Kinda silly, but if it works it works.

---

