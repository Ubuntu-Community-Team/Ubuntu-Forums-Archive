---
title: "[SOLVED] Help! I killed x11"
date: 2008-10-20
forum: General Help
---

### Post by theevilhamster on 2008-10-20
So I've gone and been a complete idiot and killed something with compiz/X11. i changed some settings in compizconfig-settings-manager, and now every time i click on something (e.g. the applications menu) where the menu should pop up, the screen goes black permanently until i restart. this happens even if i launch gnome-failsafe. i have no idea what to do! i will reinstall ubuntu if i have to, but don't really want to!
thanks **LOADS**!:(:(:(:(:(
I'm running 8.10, and would like to downgrade if possible, but all i really want is to fix this problem!
thanks again!

---

### Post by Silenus on 2008-10-20
dpkg-reconfigure xserver-xorg

Should do the trick!

---

### Post by theevilhamster on 2008-10-20
> **Silenus said:**
> dpkg-reconfigure xserver-xorg

Should do the trick!

Thanks a LOT for the help, but this did not fix my problem:(.:(:confused: in my desperation i tried ```
sudo apt-get remove compiz
``` but nothing woks still. i cannot open anything at all without parts of my screen going black!:mad: i only need to change one setting in compiz. (forget what it was called but it had a pic of a red circle).

---

### Post by medic2000 on 2008-10-20
Well for a starter you should not use a beta version. Assume its released already, still Intrepid could be buggy for some time. Use the rock solid, long time supported Hardy Heron

---

### Post by theevilhamster on 2008-10-21
Best way to downgrade? or will i have to start again from my Hardy disk?

---

### Post by theevilhamster on 2008-10-21
Never mind!: i rm'd all my config files and all is fine now:D thanks a lot anyway guys:D!.

---

