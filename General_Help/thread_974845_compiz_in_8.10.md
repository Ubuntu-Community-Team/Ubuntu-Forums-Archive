---
title: "compiz in 8.10?"
date: 2008-11-07
forum: General Help
---

### Post by grayfox444 on 2008-11-07
My graphics are acting really strange, the minimize, maximize, close buttons aren't showing up unless I mouse over them, and I can't see the option for compiz on here. 
did it not come standard this time?

---

### Post by HyperHacker on 2008-11-07
I don't think it ever came standard, just run "sudo apt-get install compiz". It's working great for me. (And if something works great for *me*, you know it'll work for you. ;))

There is a known bug with Compiz' window borders and the NVidia drivers (which I haven't even seen), but you're getting border problems without Compiz?

---

### Post by grayfox444 on 2008-11-07
i ran that and it said compiz is already the latest version, but i dont' see it anywhere.

---

### Post by grayfox444 on 2008-11-07
> **HyperHacker said:**
> 
There is a known bug with Compiz' window borders and the NVidia drivers (which I haven't even seen), but you're getting border problems without Compiz?

yeah, i put the appear settings on "off" and it went away.

though running that line of code gave me a "compiz already installed." but i can't find it in the system menu anywhere...

---

### Post by madverb on 2008-11-08
System > Preferences > Appearance > Visual Effects?

apt-get install compizconfig-settings-manager

System > Preferences > CompizConfig Settings Manager

---

### Post by grayfox444 on 2008-11-08
> **HyperHacker said:**
> 
There is a known bug with Compiz' window borders and the NVidia drivers (which I haven't even seen), but you're getting border problems without Compiz?
i have compiz running, but now i'm getting this. this bug will eventually be fixed i assume?

---

### Post by grayfox444 on 2008-11-08
also i can't figure out how to make the cube not rotate when i spin the wheel. i checked all the settings in the manager, and didn't see it. it's really bothering me :(

---

### Post by Raouf on 2008-11-08
> **grayfox444 said:**
> also i can't figure out how to make the cube not rotate when i spin the wheel. i checked all the settings in the manager, and didn't see it. it's really bothering me :(

enable Rotate Cube and of Course Desktop Cube
Alt + Ctrl + button 1 (click on your mouse) The Default to rotate
take care
- Raouf

---

### Post by BionicSeahorse on 2008-11-08
> **grayfox444 said:**
> also i can't figure out how to make the cube not rotate when i spin the wheel. i checked all the settings in the manager, and didn't see it. it's really bothering me :(

Make sure the **Viewport Switcher** plugin is enabled and check its properties. HTH

---

