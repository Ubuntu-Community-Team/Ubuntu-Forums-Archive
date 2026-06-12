---
title: "Problem after interrupted upgrade"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by sandy4linux on 2009-08-25
hello everyone,

I was upgrading my Ubuntu 8.10 to 9.04. It took pretty long time to install all the packages from internet. When it was installing the files, I just clicked the terminal icon below the update manager window, unfortunatly the update manager is closed. I tried to restart the system and a message came up indicating that, there was an error occurred, while installing Gnome-application. My shutdown icon is no more visible. I tried ctrl-alt-del it shows some unknown fonts. Please help me..............

---

### Post by P4man on 2009-08-25
try this:

```
sudo dpkg --configure -a 
```

usually works to recover from an aborted upgrade.

---

### Post by sandy4linux on 2009-08-25
I have restarted the notebook some how..now its not logging me in, when I type my password, system gets hung up and it shows localhost.localdomain// in right bottom of login screen, instead of my notebook name. I have another PC with XP installed in same Lan.... how to login to my notebook now??

---

### Post by P4man on 2009-08-25
2 ways to get back to it: when grub loads, press "escape" and select ubuntu recovery mode. In the next menu, select the root shell (I think its called). Then you'll get a terminal where you can type the above command.

If that fails (which would surprise me), your next best bet is booting off an ubuntu live CD. Then we can "chroot" into your existing install and fix it, but I'll explain  if option 1 fails.

---

### Post by sandy4linux on 2009-08-25
Hey,

I have tried recovery mode and typed command ~sudo dpkg -- command -a    in root shell.  still I could not login, but system name was corrected. I tried dpkg, instead of going to root shell, then it started downloading from where it was stopped. p4man Thanx a lot man..

---

