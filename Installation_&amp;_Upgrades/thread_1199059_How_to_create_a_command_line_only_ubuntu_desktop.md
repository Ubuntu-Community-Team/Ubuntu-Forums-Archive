---
title: "How to create a command line only ubuntu desktop"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by pythonscript on 2009-06-28
I'm creating a live CD with a few command line driven programs on it for troubleshooting other systems, and to reduce bloat, I'm looking to completely remove the ubuntu graphical interface. Which packages should I remove for this? Right now, I'm only installing partimage, clamav, and a few more anti-virus scanners for delousing people's windows partitions. I know ubuntu server doesn't have a graphical interface by default, so would it be easier just to install that and start removing packagges from it. If so, what packages could I kill from the server edition? I don't need any of the server stuff, except maybe samba, but that'll run from the command line. Thanks!

EDIT: I don't want to switch to another distro, either; it's ubuntu for me right now.

---

### Post by walter554 on 2009-06-28
I haven't tried to create a server install with non of the option boxes ticked, but it would only take you 15 mins to do so and then you could look at the amount of disk space used. If it's small enough then don't bother to reduce anything else. Verious projects (such as the linux router project) tried to create v small distros but it is very time consuming if you have an overwheming desire to get that last 10 percent.

---

### Post by vidgen13 on 2009-06-28
try removing gnome in synaptic and anything that starts with X11 or any program that runs in X and you'll have a commandline only ubuntu distro, at least that's what I think

---

### Post by confused57 on 2009-06-28
Maybe something similar to this would work:
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

or if you have access to a Window's pc and have an XP install cd, possibly ubcd4win would work to troubleshoot Windows problems.

---

### Post by ridgeland on 2009-06-28
I use System Rescue CD
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
It's a liveCD that boots to a terminal, is very small and has tons of trouble shooting tools.  You can even use startx to get to a GUI for gparted if you prefer that to parted.

---

### Post by Augsburg on 2009-06-28
I believe these packages allow for the GUI on Ubuntu:

x-window-system-core
xserver-xorg
gnome-desktop-environment

---

### Post by mcduck on 2009-06-28
> **pythonscript said:**
> I'm creating a live CD with a few command line driven programs on it for troubleshooting other systems, and to reduce bloat, I'm looking to completely remove the ubuntu graphical interface. Which packages should I remove for this? Right now, I'm only installing partimage, clamav, and a few more anti-virus scanners for delousing people's windows partitions. I know ubuntu server doesn't have a graphical interface by default, so would it be easier just to install that and start removing packagges from it. If so, what packages could I kill from the server edition? I don't need any of the server stuff, except maybe samba, but that'll run from the command line. Thanks!

EDIT: I don't want to switch to another distro, either; it's ubuntu for me right now.

The server install doesn't automatically install any servers unless you tell it to do that, so by default it gives you minimal Ubuntu setup with command-line only.

So you don't need to remove anything from it, only add the tools you want.

---

### Post by pythonscript on 2009-06-28
Thanks for all the info. I really appreciate the quick response. Being more familiar with gui's at the moment, if I install ubuntu-desktop (or maybe xubuntu-desktop) on the server edition to make configuration easier for me, then uninstall that same package, that would work too, right?

---

### Post by mcduck on 2009-06-29
> **pythonscript said:**
> Thanks for all the info. I really appreciate the quick response. Being more familiar with gui's at the moment, if I install ubuntu-desktop (or maybe xubuntu-desktop) on the server edition to make configuration easier for me, then uninstall that same package, that would work too, right?

That would be pretty much the same as installing desktop version of Ubuntu in the first place.

Also you should notice that uninstalling "ubuntu-desktop"-package doesn't remove the desktop and it's components, you'll have to uninstall all packages individually (although I remember seeing a list of all the packages you'd need to uninstall somewhere, that would make it a  lot easier..)

---

### Post by pythonscript on 2009-07-02
I actually just figured this out. Pressing F4 at the boot of the alternate install CD gives you the option to install only the command line desktop, without a graphical interface. Thanks for the help!

---

