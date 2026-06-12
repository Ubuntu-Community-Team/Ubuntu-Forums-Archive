---
title: "user permissions"
date: 2008-11-17
forum: General Help
---

### Post by belaviyo on 2008-11-17
Hi

Is it possible to add permission to special user in ubuntu konsole ?

I want to permit some user to use apt-get but I don't want to give them root access (sudo apt-get)

---

### Post by aysiu on 2008-11-17
As an admin user, paste this command into the terminal: ```
sudo env EDITOR=nano visudo
``` Then at the bottom of the file add in these lines (where *username* is the username of the special user who doesn't otherwise have administrative privileges): ```
*username* ALL=(ALL) NOPASSWD: /usr/bin/update-manager
*username* ALL=(ALL) NOPASSWD: /usr/bin/gdebi
*username* ALL=(ALL) NOPASSWD: /usr/bin/dpkg
*username* ALL=(ALL) NOPASSWD: /usr/bin/apt-get
*username* ALL=(ALL) NOPASSWD: /usr/bin/gnome-app-install
*username* ALL=(ALL) NOPASSWD: /usr/sbin/synaptic
``` Then save (Control-X, Y, Enter). That should do it.

By the way, that's kind of Gnome-specific (GDebi, Synaptic, Add/Remove). I got a little confused since you said *Ubuntu Konsole* (Ubuntu uses Gnome, but Konsole is the name of KDE terminal).

---

