---
title: "KERNEL PANIC! (on login as anyone but root)"
date: 2008-09-09
forum: General Help
---

### Post by Ubuntiac on 2008-09-09
A strange one to be sure...

I did some DV capturing as root (non gui) recently. Then when I restarted my box, everything went smooth until I put in my username and password into the KDM and hit enter. Almost immediately the screen goes black and the flashing caps lock seems to indicate a kernel panic. Nothing but a hard restart helps here (no, not even Alt+SysRQ+RSEIUB)

Strangely enough, if I boot to the recovery option and type startx, KDE starts just fine, but with the user as root.

Any ideas, team?


EDIT:
FGLRX was looking for libglx.so, and somehow I had ended up with that being a symlink to libglx.so.1 which was a symlink back to libglx.so...

I just turned both into symlinks going to libglx.so.1.3 and all is well again! \Q/ :D \Q/

---

