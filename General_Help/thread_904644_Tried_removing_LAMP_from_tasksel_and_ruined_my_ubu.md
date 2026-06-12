---
title: "Tried removing LAMP from tasksel and ruined my ubuntu"
date: 2008-08-29
forum: General Help
---

### Post by mattgaunt on 2008-08-29
Hey everyone

Basically I've accidentally un-installed everything lol, all I want to do is get my home folder off of my computer, but when ever I tried to do that the live CD it didnt work, just came up with errors saying it didn't have permission to do it.

Does anyone have any ideas? when I boot into ubuntu I get straight to a terminal.

I also tried using extfs driver in xp to copy the folder but again I didnt have permission to do it.

EEeeekk any help would be great

Gaunt

---

### Post by Oldsoldier2003 on 2008-08-29
try:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by mattgaunt on 2008-08-29
I tried that but from the command line it just said all the servers errored as if the internet isn't working. Is this due to the gnome-networking applet was uninstalled?

It connects through an ethernet cable.

---

### Post by Oldsoldier2003 on 2008-08-29
> **mattgaunt said:**
> I tried that but from the command line it just said all the servers errored as if the internet isn't working. Is this due to the gnome-networking applet was uninstalled?

It connects through an ethernet cable.

yeah it sounds like its a pretty good mess. Here is what i would do:

Boot with the live cd and mount your Ubuntu partition. Copy any critical files to a usb stick or another partition. Use sudo cp <directory_or filename> and you shouldn't get any problems with permissions, or open a root nautilus.

Any specific problems please post again.

Cheers,
OS

---

### Post by mattgaunt on 2008-08-29
Right I got internet working by command sudp dhclient and installing ubuntu-desktop which I must of un-installed through tasksel

Thanks for your help though OldSoldier

---

### Post by mattgaunt on 2008-08-29
Soz old soldier I didnt get ur reply till after I posted my last post, I got my ubuntu install back again but Im goin to do a clean install, although live CD is givin me troubles lol Not having much luck

Anyway thanks for all your help

---

### Post by Oldsoldier2003 on 2008-08-29
no worries. the important thing is you got sorted out :)

---

