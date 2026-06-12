---
title: "Modifying Keyboard Driver?"
date: 2008-10-01
forum: Hardware
---

### Post by NickLanam on 2008-10-01
Hopefully this one will be read before it ends up on page 5...

I recently moved from Fedora 8 to Ubuntu 8.04. My Ideazon MERC ([link]("http://lib.store.yahoo.net/lib/xoxide/iz-merc-keyboard-2.jpg")) was bound very nicely via xmodmap.

I can bind the red keys on the left ok now, but for some reason, in XEV, these keys and a couple others emit keyRelease events at the same time they emit the keyPress. xset r has no effect.

Does anyone know how I can get the red keys to release at the right time? I keep coming to the conclusion that I'm going to have to write my own driver, something I've found a LOOOONNNNGG tutorial on... How can I modify an existing driver and just change how the scancodes are handled?

---

### Post by NickLanam on 2008-10-01
*sigh* bump.

---

### Post by NickLanam on 2008-10-01
rebump.

---

