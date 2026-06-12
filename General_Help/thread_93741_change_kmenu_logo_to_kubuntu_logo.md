---
title: "change kmenu logo to kubuntu logo"
date: 2005-11-22
forum: General Help
---

### Post by MartinJ on 2005-11-22
How do I replace the kmenu logo (the K and gear) with the Kubuntu logo?  I know this is possible with gnome but can't find a way to do it in kde.

Thanks!

---

### Post by technoshaun on 2005-11-22
If you are referring to the standard logo in the standard KDE sign on screen go in the system settings (or kcontrol) and select "System Administration" then "Login Manager" There select Administrator Mode and you can replace the logo with anything you like by simply clicking on it and browsing to what you want.

--Shaun

---

### Post by jimmyj on 2005-11-22
Replace the kmenu.png in /usr/share/icons/your_theme/[SIZE]/apps/. Then refresh your icon set.

---

### Post by lerrup on 2005-11-23
Is there an easily available one the right siz?  I am not at my computer at the moment and can't look.

Cheers.

---

### Post by w1z4rd on 2006-06-14
[QUOTE=jimmyj]Replace the kmenu.png in /usr/share/icons/your_theme/[SIZE]/apps/. Then refresh your icon set.[/QUOTE]

How do you do this without restarting X?

---

### Post by kko1 on 2006-06-14
[QUOTE=w1z4rd]How do you do this without restarting X?[/QUOTE]

You go to System Settings - Appearance - Icons, choose your icon set and click "Apply".

Or you can:
```
killall kicker
kicker
```

:-),

kko

PS.
[QUOTE=jimmyj]Replace the kmenu.png in /usr/share/icons/your_theme/[SIZE]/apps/.[/QUOTE]

You can also create an identical & parallel directory structure below your ~/.kde/share/, so you don't have to mess with the systemwide icons.

---

