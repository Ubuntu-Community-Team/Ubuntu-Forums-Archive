---
title: "Lost sound mixer and trash bin applets"
date: 2008-10-03
forum: General Help
---

### Post by Xixor5000 on 2008-10-03
I had an issue where I rebooted my computer and the gnome panels failed to load,  after some cruising on this site I figured out how to open a virtual terminal and sudo install the gnome panels over again.  Upon reboot the panels re-appeared but my trash bin and sound mixer applets "failed to load"...OAFIID:GNOME_MixerApplet, etc.  Basically I had the same problem as this guy: [http://ubuntuforums.org/showthread.php?t=902763&highlight=mixer+applet](http://ubuntuforums.org/showthread.php?t=902763&highlight=mixer+applet) - specifically response #8 in that thread.

Does anyone have an idea how to get these two applets back?

Thanks

---

### Post by Xixor5000 on 2008-10-03
Solved the problem...
1) go to synaptic package manager
2) bottom left side of the screen click "status" button
3) highlight "Not Installed(Residual Config)" on left side
4) found the package that had to do with gnome applets and re-installed it

guess this package got screwed up when I lost the panels (which I still dont know why that happened)

---

