---
title: "deb-files and main menu entries"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by ojve on 2009-03-11
Hey!

Not sure if this is the right forum section for this, but I'll give it a try and see if someone answers me:P

I've written a small email application in python that I'm trying to make a deb-package of. I'm only just starting to learn how to make deb-packages and I've followed Jens Horst tutorial from showmedo.com (pdf available [here]("http://videos1.showmedo.com/ShowMeDos/extras/linuxJensMakingDeb/from_py_to_deb.pdf"). I've managed to get everything working except adding an entry to the gnome main-menu, even though I've tried all the different ways I can think of.

Right now the part for adding the menu-item is in the build-part of the rules-file and id looks like this:
```

mkdir -p $(CURDIR)/debian/gammamail/usr/share/applications
cp $(CURDIR)/gammamail0.3/data/gammamail.desktop $(CURDIR)/debian/gammamail/usr/share/applications
mkdir -p $(CURDIR)/debian/gammamail/usr/share/pixmaps
cp $(CURDIR)/gammamail0.3/data/gammamail.xpm $(CURDIR)/debian/gammamail/usr/share/pixmaps

```

this is the .desktop-file
```

[Desktop Entry]
Categories=Network;Email;
Comment=Access your gmail account quickly and easily!
Encoding=UTF-8
Exec=gammamail -d
GenericName=Gmail checker
Hidden=false
Icon=/usr/share/pixmaps/gammamail
Name=gammamail
StartupNotify=false
Terminal=false
Type=Application

```

I the .desktop-file copies all right, but it just won't show up in the menu! 

Any help welcome!
//T

---

