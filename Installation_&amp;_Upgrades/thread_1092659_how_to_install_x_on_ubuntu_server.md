---
title: "how to install x on ubuntu server"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by djsomi on 2009-03-10
Hi all Ubuntu fans!

I'm almost new in unix/linux systems. I have a 7.1 server edition installed and configured well. 
Now I want to install X graphical interface on this machine.
(because I need to create some virtual machine with windows system, I've planned to use vmware)

I kindly ask help from somebody who can give me a short guide how to do.


Thank you in advance,

Zoltan

---

### Post by taurus on 2009-03-10
I assume you want to run Gnome--ubuntu-desktop.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

