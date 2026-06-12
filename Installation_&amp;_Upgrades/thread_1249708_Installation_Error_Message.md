---
title: "Installation Error Message"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by chome4 on 2009-08-25
Trying to install a previously working program to get the newer version and get the error message shown.

It mentions only one package installer is allowed to run. As far as I know I'm using the Deb installer.

Can someone tell me how to follow those instructions given.

---

### Post by P4man on 2009-08-25
you have another program open that you must close first. Add/remove programs or synaptic package manager most likely. Close those first, then try again. If you are sure nothing else is running, then maybe its a lockfile that needs removing. Rebooting is probably as easy though.

---

### Post by chome4 on 2009-08-25
I've restarted the machine and no other stuff referred to is running!

---

### Post by P4man on 2009-08-25
ok, apparently an aborted install or upgrade can cause that message to. You need to fix that first.

try running:

```
sudo dpkg --configure -a
```

If that gives a similar error, you will have to reboot, press escape in grub menu, select ubuntu recovery mode, select root shell, and rerun the above command.

---

### Post by chome4 on 2009-08-25
Works now. 

Thanks for that.

---

