---
title: "Export non-core OS packages and configuration"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by zsugiart on 2009-04-09
Hi all, 

It took me almost 1 month to get my current Ubuntu (8.10) to be my perfect desktop workstation. Back then, I use to think that Linux is cool, but not very usable yet, but now I've been on my Ubuntu full time and I don't feel the urge to go back to Windows. 

And then the thought came to me: On the next Ubuntu, would I need to repeat all this installation, settings and what not all over again? Mind you, setting stuff in Ubuntu sometimes involves googling for the subtle ways of manual editing of config files. It can be very time consuming.

I've spoken with a lot of my UNIX friends about this, and apparently upgrades have always caused them grief. Because we have to do all the setup all over again. 

Is there a way to "extract" all of your installed packages, compiz, nautilus, networs, mounts, users, etc configuration off UBUNTU. This way if and when I upgrade/install a newer version of ubuntu, my non-core OS stuffs can be imported back?

---

### Post by pbotros1234 on 2009-04-09
To backup:

```
sudo dpkg --get-selections > dpkg.packages.backup.txt
sudo gconftool-2 --dump / > gconfpreferences.backup.xml
```


To restore in the future:

```
sudo dpkg --set-selections < dpkg.packages.backup.txt
sudo apt-get -u dselect-upgrade
sudo gconftool-2 --load gconfpreferences.backup.xml
```

---

