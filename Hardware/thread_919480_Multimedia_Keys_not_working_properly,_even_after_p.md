---
title: "Multimedia Keys not working properly, even after playing with xmodmap"
date: 2008-09-14
forum: Hardware
---

### Post by NickLanam on 2008-09-14
Hopefully this one will be read before it ends up on page 5...

I recently moved from Fedora 8 to Ubuntu 8.04. I've always loved Fedora, used it since 6, and had a nice little group of files to use xmodmap and gconf to change the keybindings of my Ideazon MERC ([link]("http://lib.store.yahoo.net/lib/xoxide/iz-merc-keyboard-2.jpg")).

In normal (as in not while I'm playing a game) keybindings, I was able to remove the binding from the number keys to listen to their keySym in metactiy for shortcuts. No such luck now, unbound keys have no keysym :(

But my big issue is with the red keys on the left. I can bind them OK, but for some reason, in XEV, these keys among my multimedia keys emit keyRelease events at the same time they emit the keyPress. Naturally, this causes problems with repeating even after xset r.

Does anyone know how I can at least get the red keys to release at the right time so I can play my games again?

---

### Post by NickLanam on 2008-09-15
Bump.

---

### Post by NickLanam on 2008-09-18
Bump.

---

### Post by NickLanam on 2008-09-20
Bump.
Does anyone read these before 1,000,000 more get posted?

---

### Post by OrelEagle on 2008-12-26
Hi,

I don't really understand your problem, but you can always try [xbindkeys]("http://hocwp.free.fr/xbindkeys/xbindkeys.html") for custom hotkeys...

---

