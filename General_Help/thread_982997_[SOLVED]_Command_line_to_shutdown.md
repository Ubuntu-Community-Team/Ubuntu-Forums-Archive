---
title: "[SOLVED] Command line to shutdown"
date: 2008-11-15
forum: General Help
---

### Post by jesuisbenjamin on 2008-11-15
Hello forum,

I am looking for a command line to prompt me with the traditional "shut down your computer window" so i can make a choice as to what to do next (i.e. reboot, shut down etc.)
I know of the command line 'shutdown' but this does not prompt me with the friendly shut down window...

Anyone could tell please?

---

### Post by CatKiller on 2008-11-15
gnome-session-save --shutdown-dialog

---

### Post by vishzilla on 2008-11-15
shutdown -h <time> (for example: now, +N mins, hh:mm)
shutdown -r <time> to reboot

---

