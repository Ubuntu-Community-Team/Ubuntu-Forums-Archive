---
title: "Ubuntu crashes at startup- quick fix? help!"
date: 2008-10-09
forum: General Help
---

### Post by CharonM72 on 2008-10-09
When I log in to GNOME normally (which is by running the Xclient script) it all goes fine for a few seconds and the makes an error noise and the top and bottom panels disappear. The desktop is still there, but if I try to do anything the desktop icons disappear and it says, "Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem." This doesn't work though. Every ten seconds or so the error noise reappears too.
HOWEVER, in failsafe GNOME, the same problem happens (once, but does not recur) and by doing as the error message says I am able to fix it. It looks to me like there's a program which runs on startup and continually crashes the bonobo-activation-server and/or nautilus. Any ideas?

EDIT: By stopping bonobo-activation-server or gnome-panel it will stop the error noises. Of course, it doesn't get me anywhere either. Killing either of them just makes them restart and continue the same process.
There seems to be a problem relating to the ccin_load_system_glossary function. Whenever I try to run anything through the terminal, it always comes up with an error relating to that saying that there is no file or folder of that type, and then it crashes. Maybe that's the problem? If not it likely has something to do with gnome-panel, because that is what's crashing over and over.

---

### Post by fsmithred on 2008-10-10
This probably won't help much, but recently, I've gotten the same Nautilus error message in debian lenny. The only real problem I've noticed is that I can't rename a file in Nautilus, but I can do it in a terminal. If I log out and log in again, it's ok.

---

### Post by CharonM72 on 2008-10-16
Uninstalled SCIM and it fixed it. Still have yet to figure out how to fix SCIM.

---

