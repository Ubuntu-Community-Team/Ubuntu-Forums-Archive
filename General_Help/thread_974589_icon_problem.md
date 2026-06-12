---
title: "icon problem"
date: 2008-11-07
forum: General Help
---

### Post by _Q_ on 2008-11-07
I experimented a bit (in Hardy Heron), and deleted some of the themes and icons in /usr/share dir (don't ask why, lol).
I've lost pretty much all the icons, and reinstalled "gnome-icon-theme" package which restored most of the icons. I'm still missing icons for bluetooth, network manager, pidgin in nautilus-panel, and several more in the menus.

Does anyone know which packages to reinstall to gain these icons? (already tried reinstalling the basic packages - pidgin, network manage, etc, no effect)

---

### Post by CatKiller on 2008-11-07
You could try re-installing ```
ubuntu-artwork
gnome-themes
tangerine-icon-theme
```

---

### Post by _Q_ on 2008-11-08
I did, still don't see icons for network manager (who is reporting an error on every startup), bluetooth, pidgin, assistive technologies, network proxy, etc...:(

---

### Post by CatKiller on 2008-11-08
Are they panel icons that aren't displaying? Have you removed the Notification Area from your panel?

It's the pidgin-data package that has the icons in. Similarly, it's bluez-gnome. I don't know which package has the Assistive Technologies icons.

---

### Post by _Q_ on 2008-11-08
Pidgin, network manager and bluez are panel icons that are missing.
Other are menu icons...

Already tried to reinstall bluez-gnome.. doesn't help..

It seems I'll have to reinstall ubuntu :(

---

### Post by CatKiller on 2008-11-08
> **_Q_ said:**
> Pidgin, network manager and bluez are panel icons that are missing.

Right-click on the panel, select Add to Panel... and add in the Notification Area.

---

