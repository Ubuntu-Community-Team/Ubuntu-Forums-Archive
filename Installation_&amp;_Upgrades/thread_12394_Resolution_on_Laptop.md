---
title: "Resolution on Laptop"
date: 2005-01-24
forum: Installation &amp; Upgrades
---

### Post by may1950 on 2005-01-24
Hi - I just installed Hoary on my PC desktop and son's laptop (Toshiba M30 with NVIDIA GeForce GO FX 5200 64MB).  No problem with the installations.  However, we cannot adjust the resolution on the Toshiba M30.   There's only setting available from the menu (640 x480 with 60 HZ).  Any ideas as how we can adjust the resolution on the laptop?

Much appreciated.

---

### Post by jensyt on 2005-01-24
[QUOTE=may1950]Hi - I just installed Hoary on my PC desktop and son's laptop (Toshiba M30 with NVIDIA GeForce GO FX 5200 64MB).  No problem with the installations.  However, we cannot adjust the resolution on the Toshiba M30.   There's only setting available from the menu (640 x480 with 60 HZ).  Any ideas as how we can adjust the resolution on the laptop?

Much appreciated.[/QUOTE]
As far as I'm concerned, you should be able to manually change the values acceptable in your XFree/Xorg config(/etc/X11/XF86Config-4 or /etc/X11/xorg.conf) with any text editor (must have permission, via sudo or logged in as root). Look for the section labeled

```
 Section "Screen"
    Identifier  "Screen 1"
    Device      "GFX ATI Radeon"
    Monitor     "19 inch"
    DefaultDepth 24

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
```

Just do like I've got and add the resolutions you want in there. Also, neglect the information in quotes for identifier, etc, your's will most likely be different. As for the refresh rates, that should be:

```
Section "Moniter"
   HorizSync   31.5-93.8
   VertRefresh 60-100
```

You need to know exactly what your moniter can do...

---

