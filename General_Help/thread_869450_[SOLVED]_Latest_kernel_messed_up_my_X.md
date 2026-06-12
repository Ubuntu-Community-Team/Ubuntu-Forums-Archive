---
title: "[SOLVED] Latest kernel messed up my X"
date: 2008-07-24
forum: General Help
---

### Post by spadewarrior on 2008-07-24
Or at least, I think that's what did it.

Today I installed the automatic update containing kernel 2.6.24.20. Before getting to the login screen, I'm told that x is running in low-graphics mode, locked at 800x600 resolution. 

On logging in, I went to nvidia-settings to try and change the resolution. No dice.

Has anyone else had any problems with this?

I can still use .19 perfectly well, so I assume something in .20 doesn't get on with my system.

Any solutions to try out, or should I wait and see if another update comes and fixes it?

Thanks.

---

### Post by drs305 on 2008-07-24
Can you change the resolution with:
```
gksu displayconfig-gtk
```

---

### Post by sdennie on 2008-07-24
How did you install the nvidia drivers?  If you've manually installed them by downloading from the nvidia website, whenever you install a kernel update that increments the version number, you will have to re-install the nvidia drivers.  You can prevent that from happening in the future using this guide: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by spadewarrior on 2008-07-24
Ah, that'll be it then. I used Envy-NG for the nvidia drivers.

Thanks for the link!

---

### Post by sdennie on 2008-07-24
I'm not sure how envyng handles kernel updates but, if that's what you are using, you might try to just re-install the drivers with envyng again.  The guide posted above won't work with envyng.

---

### Post by drs305 on 2008-07-24
I use EnvyNG with an older (GS 7600) card and don't recall having any video issues with any of the hardy kernel updates. I am currently using -19 and have not upgraded to 20.

---

### Post by spadewarrior on 2008-07-25
I've only had trouble with .20, so you might have to reinstall the drivers after upgrading. I've done this now and all is back to normal.

---

