---
title: "Cannot delete &quot;awn-manager&quot; launcher"
date: 2008-09-06
forum: General Help
---

### Post by phil81uk on 2008-09-06
I reinstalled Ubuntu today, fresh install, and installed AWN. All works well, but there is a launch called "AWN Manager" which launches the AWN Manager. I cannot delete this Launcher. In AWN Manager, I highlight it, press Remove, and it disappears but upon restarting AWN it is still there.

I went to .gconfig/apps/avant-window-navigator/%gconfig.xml where there is a list of launchers. I deleted it manually, but same happened again... it reapppeared when I restarted AWN.

---

### Post by slimg00dy on 2008-09-06
Have you tried going to synaptic and searching to "Avant Window Navigator" and removing it from there?

---

### Post by Major Crash on 2008-09-21
He wants to keep AWN, but he wants to get rid of a launcher that shows up on the actual dock.  I've been having the same problem.

---

### Post by phil81uk on 2008-09-22
Exactly. The attached screenshot highlight a useless icon which seems to do nothing at all and I cannot remove in in my Dock Preferences.

---

### Post by dismal_denizen on 2008-10-11
The "Launcher/Task Manager" applet requires at least one launcher to be listed. To remove that useless icon you have 2 options:

1. Add a new launcher for something and delete the awn-manager one.
2. If you don't want any launchers, remove the "Launcher/Task Manager" applet and add "Standalone Taskmanager" instead.

---

