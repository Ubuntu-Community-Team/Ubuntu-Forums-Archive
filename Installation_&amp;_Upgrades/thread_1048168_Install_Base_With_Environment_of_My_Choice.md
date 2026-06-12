---
title: "Install Base With Environment of My Choice?"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by Tayl on 2009-01-23
Hello all.

Right, I'm planning on installing Ubuntu again on my laptop and just wondered if there was any way I could install the base of Ubuntu but instead of having Gnome installed on top of it, avoid the Gnome install and manually install my own choice of desktop environment (such as Fluxbox etc). Also, what other desktop environments are there these days? It's been a while since I last used any Linux distro properly.

Any help on this would be greatly appreciated.

Best regards,

Tayl.

---

### Post by Partyboi2 on 2009-01-23
You can use [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by Tayl on 2009-01-23
Thank you for the response Partyboi.

Is there no possible way to do it with the newest regular release of Ubuntu via any sort of command install? Because I have that on CD ready. Also, another quick question, is there any possible way to install Ubuntu normally (via the GUI install with Gnome) without all of the clog that it comes with (such as the games, software I won't use such as Torrent clients, IM clients etc)?

Tayl.

---

### Post by Partyboi2 on 2009-01-23
You could use the live cd to install then remove the packages you don't want to install eg
```
sudo apt-get remove gnome-games
``` will remove the games from gnome.
Or you could remove the gnome desktop and replace it with what you like, but probably easier to use the alternate cd and install by cli option what you want.

---

### Post by ajgreeny on 2009-01-23
The simple answer is "no"; there is no way to choose what is included if you use the live CD to install the system.  You should be able to do it with the alternate install CD as linked to by partyboi2.

---

### Post by snowpine on 2009-01-23
Here is another good tutorial:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

FYI you can install the base CLI Ubuntu using either the alternate CD or the mini.iso CD, which is only a 10mb download.

---

