---
title: "KDE 3.5 - Missing Menu Items"
date: 2005-11-30
forum: General Help
---

### Post by jonesy on 2005-11-30
I've noticed that after installing KDE 3.5 (and even the previous version), that there are no menu items for several packages.   Most noticeably, there are no menu items for KMail and the KDE Control Center.  Why aren't these created by default when the package is installed?

---

### Post by Chris180775 on 2005-11-30
I have the same problem with kmail, does anyone know how to fix this?
Bye

---

### Post by magnusbb on 2005-11-30
I experience the same on my Ubuntu box with Kubuntu KDE 3.5 packages. There are menu entries for these applications in GNOME however - so for me as a GNOME user it is a minor issue.

---

### Post by nikolai.m on 2005-11-30
did you notice there is no more "Actions->open here terminal" in right click menu.

---

### Post by Xian on 2005-11-30
[QUOTE=nikolai.m]did you notice there is no more "Actions->open here terminal" in right click menu.[/QUOTE]
That can be reset by installing the nautilus-open-terminal package.

---

### Post by jonesy on 2005-12-01
I know you can manually add menu items using the KDE menu editor, but come one, the Control Center and Mail client not having menu entries after installing the packages?  That's a little unreasonable if kubuntu is your default distro don't you think?

---

### Post by mlomker on 2005-12-01
[QUOTE=jonesy]I know you can manually add menu items using the KDE menu editor, but come one, the Control Center and Mail client not having menu entries after installing the packages?  That's a little unreasonable if kubuntu is your default distro don't you think?[/QUOTE]

The control center doesn't have an icon in Breezy, in general.  They are planning to transition entirely to System Settings, but clearly they haven't duplicated all of the functionality yet so not sure why they don't leave an icon.

The kmail icon is probably just a packaging error.  I actually didn't notice because I always launch it from Run Command anyway.

---

### Post by cdhinch on 2005-12-03
Okay, there is an easy fix for the Control Center.

Right click on the K-Menu.
Select Panel Menu -> Configure Panel.
Go to Layout -> Menus.
In the Optional Menus box put a check mark in the box next to Preferences.
Click OK.

Now when you open the K-Menu there will be a new menu item under Actions called Preferences.  You can then open up the Control Center or any of the individule configuration modules from that menu.

Charles

---

