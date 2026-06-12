---
title: "What if I don't want the panels?"
date: 2008-09-19
forum: General Help
---

### Post by mishathegoat on 2008-09-19
Hello everyone,

I use only one panel and only because it has the "Main Menu" launcher.. I use the AWN dock bar to list my windows.

I was wondering if there was an alternative to the gnome panels or a screenlet or anything that would help me to move away from them..

Please any any any ideas or suggestion no matter how strange are appreciated.

Thanks,

Misha

---

### Post by jonian_g on 2008-09-19
AWN has a menu applet. So you can remove the panels and access the menu from there.

---

### Post by Ripfox on 2008-09-19
Delete them? Use Fluxbox? ;)

---

### Post by mishathegoat on 2008-09-19
I do love fluxbox's simplicity but lets say I had issues with my wireless card or some other thing, it's MUCH harder to troubleshoot it in fluxbux then gnome..

EDIT: Anyone know where to get these AWN applets?

---

### Post by jonian_g on 2008-09-19
First remove awn from synaptic.
Then do the following:

Works for both 32-bit and 64-bit architectures, but not PowerPC. 

Add these lines to a new file/etc/apt/sources.list.d/reacocard-awn.list:

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) hardy main

Warning: You'll most likely get a warning about no public key (or something similar). This is a known bug in Launchpad and is slated to be fixed.

Now to install AWN: 
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

---

### Post by anotherdisciple on 2008-09-19
> **jonian_g said:**
> First remove awn from synaptic.
Then do the following:

Works for both 32-bit and 64-bit architectures, but not PowerPC. 

Add these lines to a new file/etc/apt/sources.list.d/reacocard-awn.list:

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) hardy main

Warning: You'll most likely get a warning about no public key (or something similar). This is a known bug in Launchpad and is slated to be fixed.

Now to install AWN: 
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

+1

I use these... and they are great. I just hide my gnome panel because you can't get rid of the last one. PyNot is the applet that made me able to get rid of my gnome-panel

---

### Post by c2rjay on 2008-10-08
Want to bring this up again. I followed the guide to get the applets. But the Avant Navigator Bar doesn't show up, the manager is there, and has the applets, but no bar and no launcher at Applications>Accessories. So i went to Synaptic and notice that avant-window-navigator-bzr wasn't installed. So i tried to install it, and i get this error - 

> E: /var/cache/apt/archives/avant-window-navigator-bzr_0.3.1.bzr482.1~hardy_i386.deb: trying to overwrite `/usr/share/locale/id/LC_MESSAGES/avant-window-navigator.mo', which is also in package avant-window-navigator-data


Any suggestions? I had the original AWN installed, and i uninstalled it, following the guide, and the avant-window-navigator-bzr doesn't want to install.

---

