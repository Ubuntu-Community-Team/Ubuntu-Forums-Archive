---
title: "no GUI"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by linuxhopefull on 2009-04-16
I installed Ubuntu and all I get is my username and passwd. I'm learning CLI but I can't the GUI to come up

---

### Post by taurus on 2009-04-16
Did you install the server version or the desktop version?  

What happens when you run this command from a prompt, after you've logged in?

```
startx
```

---

### Post by linuxhopefull on 2009-04-16
server...I treid it and it had me install xinit. after that it returned an error /user/bin/x11/x not found

---

### Post by taurus on 2009-04-16
If you installed the server version, then console is all you get.  If you want to have Gnome desktop environment, you now need to install it.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

