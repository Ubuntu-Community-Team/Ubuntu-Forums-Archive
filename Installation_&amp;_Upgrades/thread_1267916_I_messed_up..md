---
title: "I messed up."
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by DRNewcomb on 2009-09-16
OK. I messed up. This is dumb. 

I was trying to get a package (Qwt5) to work and tried installing python 3.0 and removing python 2.6. I didn't think it would be a big deal but it looks like the whole world depends on python 2.6. The Synaptics Package Manager removed a bunch of stuff and now I'm down to a text-only login. The good news is that I have a working system, networking and all my data files intact. I can actually run "startx" or "xinit" and get a basic X11 screen.

Can anyone give me some suggestions on how to reinstall the basic Ubuntu user environment from this point. Maybe I could start the package manager from the command line and reinstall the key items I deleted? I'd prefer to not reinstall the whole system if that would wipe out what I already have.

I'm running 9.04 and don't have any current backups.

---

### Post by Stunts on 2009-09-16
Try doing a sudo apt-get install ubuntu-desktop.

That will probably fix things...

You can also try to remove python3 and reinstall python2.6...

Let us know if it worked =-) Good luck.

---

### Post by DRNewcomb on 2009-09-16
Thanks. That one-line command did it. I'm sorry to say that I have been using the GUI for so long that I forgot the command line version. 

I actually had reinstalled python 2.6. After I uninstalled it the system continued to work and I tried reinstalling many things. However, when I logged off I could not log back on. It seems I had not reinstalled enough.

Thanks again.

---

### Post by gradinaruvasile on 2009-09-16
Could not login or text only? startx helps?

---

### Post by Stunts on 2009-09-16
Glad that it's sorted.

If you need anything else just call back. =-)

---

### Post by DRNewcomb on 2009-09-16
> **gradinaruvasile said:**
> Could not login or text only? startx helps?Perhaps I was not quite clear. Once I logged out I could not get back to the Ubuntu desktop, text login only. I could run X11 only in a very dumb mode. Perhaps I could have started a window manager and run the GUI but I forgot how. The apt-get command fixed the problem. Thanks.

---

