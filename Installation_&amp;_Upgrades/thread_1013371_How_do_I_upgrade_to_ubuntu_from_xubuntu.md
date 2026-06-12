---
title: "How do I upgrade to ubuntu from xubuntu?"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by Bluehotdog5 on 2008-12-16
I have compiz but it wont work with xfce, I need gnome

---

### Post by squeabs on 2008-12-16
xfce and gnome are two different desktop environments. I would suggest burning a copy of ubuntu and installing it fresh from the cd. That'll get you the best, least buggy install.

---

### Post by mrbiggbrain on 2008-12-16
you can install gnome, then uninstall xfce, i douno the exact commands, but uninstall xfce under gnome and it should work out ok.

---

### Post by taurus on 2008-12-16
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by lewisskinner on 2008-12-16
> **taurus said:**
> ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

I second this, but if you also want rid of Xfce/xubuntu completely, then

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get remove --purge xubuntu-desktop
```

---

### Post by mrbiggbrain on 2008-12-16
quick question, i have KDE4 installed, and never use gnome, but use some GTK applications with my KDE install (i know i know iv been a bad boy) will uninstalling gnome, also uninstall the required files to run these applications? of so can they be reinstalled without gnome?

---

### Post by lewisskinner on 2008-12-16
You really ought to start a new thread fo this, but...

If the GTK apps are dependencies of the Ubuntu-desktop metapackage, then ```
sudo apt-get remove --purge ubuntu-desktop
``` may remove these packages, but omitting the '--purge' component may work.

However, if the apps are dependant *on* the ubuntu-desktop package, they may well stop working.

Best thing is to make a note of the packages you want, and then reinstall them afterwards using ```
sudo apt-get install *xxxx*
```

Or, use the package GUI to remove the ubuntu-desktop?

---

