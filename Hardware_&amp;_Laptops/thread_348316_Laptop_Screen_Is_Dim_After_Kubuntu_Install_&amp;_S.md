---
title: "Laptop Screen Is Dim After Kubuntu Install &amp; Suspend"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by borris.morris on 2007-01-28
Ok, here's the situation. Everything worked perfectly until I recently install kubuntu by, "sudo aptitude install kubuntu-desktop" and all worked well except when I suspend or change sessions through ctrl+alt+function key (f1,f2,etc). When I come back to my original session, the laptop screen is very dim, the only way to solve this is to restart my session. So I uninstalled kubuntu and did a restart, and it still didn't work. The only way I can think of to fix it is to update. Any help would be greatly appreciated and I'll post on how my update goes.

---

### Post by borris.morris on 2007-01-28
bump

---

### Post by borris.morris on 2007-01-28
bump

---

### Post by borris.morris on 2007-02-03
bump

---

### Post by Cactus Sediento on 2007-02-05
same problem here

---

### Post by borris.morris on 2007-02-06
Really weird, huh. It's a pain in the butt!

---

### Post by ramjet_1953 on 2007-02-07
Does your lappy have hardware keys to set screen brightness up and down?

My Acer TravelMate 4101 has Fn+ keys to control brightness, sound, touchpad, sreen blanking and screen switching, all of which work fine under 6.10.

Regards,
Roger :cool:

---

### Post by borris.morris on 2007-02-07
nope, it doesn't. again the only way to solve it is to start a new session through ctrl+alt+backspace or restarting. really odd.

---

### Post by ltmon on 2007-02-07
Try the guidance power manager applet. - it should be in your system tray if Kubuntu installed correctly.  Click on it and check the brightness settings.

If this doesn't help, try restarting the guidance power manager, and see if that has been screwing around with your brightness:

Hit alt-f2 and:
```

killall guidance-power-manager.py && guidance-power-manager

```

should do it for you.

---

### Post by borris.morris on 2007-02-09
I doubt that will work. I reinstalled Ubuntu Edgy with Gnome only. I really like the customization of KDE though. Any other help. Again the only way was to restart or start a new session. Anybody else try this as I don't feel like having to reinstall Edgy again.

---

### Post by borris.morris on 2007-02-10
any other ideas. again i dont want to install kde until im 100% sure it will work.

---

### Post by borris.morris on 2007-02-10
well, i decided to try to install kde. hoping for the best.

---

### Post by borris.morris on 2007-02-10
nope, after a restart it is broken again. trying an update.

---

### Post by borris.morris on 2007-02-10
figured out one other thing i changed. my video driver from neomagic to vesa. i'm trying to switch back, but then my menus will have lines. oh well.

---

### Post by borris.morris on 2007-02-10
that was my problem. except kde is way ugly. look at the taskbar. pics are what its like before suspend and then after.
well, at least the after i selected the neomagic driver.

---

### Post by borris.morris on 2007-02-12
Well, it's definitly the vesa driver thats to blame. Switched back to neomagic and it works perfectly.

---

