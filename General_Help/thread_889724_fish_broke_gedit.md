---
title: "fish broke gedit"
date: 2008-08-14
forum: General Help
---

### Post by gunksta on 2008-08-14
After installing the fish terminal, which I think I rather like, and setting it as my default shell, gedit stopped working. It doesn't matter if I start gedit from a terminal or Alt-F2 or the menu.

From a terminal, I type in gedit and wait. There are no errors, there is no gedit window. My hard drive spins a little. If I wait long enough, a completely blank window will appear. I can see where the text canvas is (it's white) and the rest of the window is grey. There are no icons, no nothing. The title bar works correctly, and lists gedit as having a blank file open.

When I used gnome-system-monitor, I can see that when I try to start gedit, it starts a command called gnome-pty-helper. Gedit is killing off 8-11% of my CPU and needs 12 megs of ram. 

When I change my shell back to bash, gedit works normally. So, gedit works, but not with the fish shell.

Any ideas?

---

