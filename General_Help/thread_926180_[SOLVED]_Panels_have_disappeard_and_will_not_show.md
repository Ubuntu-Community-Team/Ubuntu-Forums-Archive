---
title: "[SOLVED] Panels have disappeard and will not show"
date: 2008-09-21
forum: General Help
---

### Post by mhedges48 on 2008-09-21
Hello, my panels have disappeared. I have tried 
apt-get --reinstall install ubuntu-desktop
as well as purging gnome-panel and reinstalling, etc., with no luck... when I try and run gnome-panel from the terminal, it says "A panel is already running".

I used to have two panels, one on the bottom left corner and the other on the bottom right (with AWN in the middle). Now I just have AWN and not panels... any ideas on how to get them back?

thanks!

---

### Post by mhedges48 on 2008-09-22
The problem was the gconf settings (they remained even after purging/deleting gnome-panel and reinstalling). 

It was fixed by:
apt-get remove gnome-panel
Deleted the panel directory from .gconf
apt-get --reinstall install ubuntu-desktop

---

