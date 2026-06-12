---
title: "Taskbar disappeared after update"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by delightt on 2009-01-29
I ran a bunch of updates last night including new kernel (linux-generic, linux-headers, etc.) gnome-power-manager, etc.

I also removed evolution.

When I rebooted the system as recommended, my taskbars had disappeared. I don't appear to have any other problems. Any idea how I can get them back?

I'm using 8.10.

---

### Post by x33a on 2009-01-29
press alt+f2 and type gnome-panel.

or if this doesn't work, 

try

alt+f2 type gnome-terminal 

and type killall gnome-panel in the terminal.

---

### Post by delightt on 2009-01-29
Thanks, I did this other thing I found on the forums:[http://ubuntuforums.org/showthread.php?t=1039739]("http://ubuntuforums.org/showthread.php?t=1039739")
(rm -rf .gnome .gnome2 .gconf .gconfd .metacity) - reset gnome settings.

It removed all my settings, and I couldn't get online (via wifi).

I'm now doing sudo apt-get install ubuntu-desktop (on lan cable), and it's reinstalling evolution, so I guess that's what it was.

---

### Post by john stiles on 2009-02-22
I had the exact same problem after updating and removing evolution.

Removing evolution also removes the gnome-panel. Reinstalling gnome-panel reinstalls the evolution data server. Typing Gnome-panel in xterm started the task bars with my old settings. Shut down with xterm and gnome-panel running, and it restarts all okay.

Anyone having problems starting xterm (no menu or shortcut working) can search for it in a nautilus desktop folder and execute from there. Or, log out, then in bottom left of screen choose another flavour where GUI is functioning and fix from there.

---

