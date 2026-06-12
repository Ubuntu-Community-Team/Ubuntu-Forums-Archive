---
title: "No icons &amp; mouse action on desktop"
date: 2008-09-14
forum: General Help
---

### Post by embeemb on 2008-09-14
Right after I installed Hardy, all the icons disappeared from the desktop. There's no mouse action either. Gnome panel is where it should be and working fine. When I start Nautilus as root, only shortcut icons appear on the desktop, but none of the files/folders in ~/Desktop.

Any ideas?

---

### Post by iaculallad on 2008-09-14
Press Alt+F2 combo key and input "gconf-editor" (that's w/o quote). Configuration editor will open and navigate to apps->nautilus->desktop, place a check value on the item you want to display on your desktop. Close the gconf-editor window.

---

### Post by embeemb on 2008-09-14
Thanks for the reply. Trash, Network, Home & Computer all had check marks next to them.. Anything else that might be the culprit ?

---

