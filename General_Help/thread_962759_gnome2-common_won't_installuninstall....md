---
title: "gnome2-common won't install/uninstall..."
date: 2008-10-29
forum: General Help
---

### Post by DiGiTGOD on 2008-10-29
I'm getting an error when I try and install the gnome2-common component via apt-get or adept in Kubuntu...

It says:

Commit failed.
To continue, hit ok and we will try to recover. If you close the application now, we will not do anything and you may try to resolve the problem manually.
(If you suspect this is a bug in Adept, please also provide the following exception description in the report).

The error was: 
APT Error. Context:
    Running dpkg, 
    [ /usr/bin/dpkg, --status-fd, 3, --force-depends, --force-remove-essential, --remove, libgnome2-common, libgnomevfs2-common ], 
    Sup-process returned error code 1, 
    Error processing libgnome2-common : Package is in a very bad inconsistent state - you should.

When I try to remove it from Adept... and it's flagged as "upgradeable" in adept...

Whenever I try and install anything like Vuze or anything it requires me to install the above... and then I get another error something about dgettext and GConf2 or something...

Is there a way for me to remove forceably, then try to reinstall??

Any help much appreciated..

Martin

---

### Post by Kevbert on 2008-10-29
Try
```
sudo dpkg --configure -a
sudo apt-get install -f
```
in Konsole.

---

### Post by DiGiTGOD on 2008-10-29
Thanks for the quick reply...

I tried it and got this error after the first command...

martin@FRED:/usr/lib$ sudo dpkg --configure -a
Setting up gconf2 (2.24.0-0ubuntu1) ...
gconf-merge-tree: symbol lookup error: gconf-merge-tree: undefined symbol: g_dgettext
dpkg: error processing gconf2 (--configure):
 subprocess post-installation script returned error exit status 127

anymore ideas?

Martin

---

