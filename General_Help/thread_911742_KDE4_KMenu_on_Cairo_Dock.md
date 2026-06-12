---
title: "KDE4 KMenu on Cairo Dock"
date: 2008-09-05
forum: General Help
---

### Post by edvar on 2008-09-05
Does anyone know how to put the KDE4 KMenu on the Cairo-Dock?

---

### Post by fabounet on 2008-09-08
if you can read french, take a look here [http://www.cairo-dock.org/ww_page.php?p=Cairo-dock%20sous%20KDE%203.5&lang=fr]("http://www.cairo-dock.org/ww_page.php?p=Cairo-dock%20sous%20KDE%203.5&lang=fr")
sorry it's not yet translated into english.

basically you just create a manual launcher, that will have this command :
dcop kicker kicker popupKMenu 0

---

### Post by edvar on 2008-09-08
I read something about it but it's for KDE 3.5 and I'm using KDE 4.1. Anyway I'll give it a try and see if it works. Thanks!

---

### Post by fabounet on 2008-09-08
ah sorry I read too quickly, there is no more dcop in KDE4.
maybe some DBus alternative ?
otherwise, if you can make the menu appear with a keyboard shortcut (for instance ALT+F1), then you can just make a manual launcher with 
  ALT<F1>
as the command, and you're done ;-)
if you want it to appear above the icon instead of the usual place, you'll have to remove the Menu from your KDE panel.
That's the method under Gnome for the moment, it may work for KDE too.

---

### Post by edvar on 2008-09-09
Thanks but it didn't work. As expected the DCOP command didn;t work as KDE4 uses DBUS. I tried to do it via keyboard shortcuts but also didn't work. I tried to install Lancelot and checked its keyboard shortcut as well (ALT+F5)... no luck!

Does anyone have any other ideas? I could try a similar DBUS command to see if it would work. Does anyone know the command?

---

### Post by edvar on 2008-12-08
Bump!

---

### Post by fabounet on 2008-12-09
the GMenu applet should do the work for KDE too

---

### Post by edvar on 2008-12-09
I'm not running any Gnome app on my Kubuntu, no Gnome Desktop Environment installed. Also I checked and there's no GMenu applet on Cairo-dock (this confirms: [http://ubuntuforums.org/showthread.php?t=999475]("http://ubuntuforums.org/showthread.php?t=999475")). 

Any other ideas?

---

### Post by Farmer of Bricks on 2008-12-10
you could try creating a .desktop file with the exec to open the menu in it. I don't know much, but it might look like this:
```

[Desktop Entry]
Icon=KMenu
Name=KMenu
Type=Application
Exec=COMMAND

```
where COMMAND is the command to open Kickoff or the Kmenu or Lancelot

---

### Post by edvar on 2008-12-11
Well, it doesn't help much since I'm trying to find out what command calls the menu... Any ideas?

---

### Post by fabounet on 2008-12-12
the 64bits packages was not built with the GMenu applet (no good reason for that)
you can try to install it manually, or try to find another plug-ins package that contains it.

---

### Post by edvar on 2008-12-13
I am not using 64 bits. I have Kubuntu Intrepid 8.10 32 bits.

Other than that I appreciate the GMenu suggestion but I am a KDE person and really like the KDE4 Menu. As far as I understood, GMenu would give me a Gnome menu. Since I don't have (and don't plan to) any Gnome packages installed on my system, I think it wouldn't help. 

So, as far as the KDE4 Menu is concerned, is there a way to put it on the Cairo Dock?

---

### Post by fabounet on 2008-12-15
GMenu will give you the same menu you have with KDE (because KDE's menu is XDG compliant) , but with the Gnome look.
if it doesn't suit you, probably you can call the menu with a shortcut like alt+F1 ? or maybe you can look for a dbus command.
I don't know KDE enough.

---

