---
title: "Nothing will open"
date: 2008-08-07
forum: General Help
---

### Post by stealth17 on 2008-08-07
For some reason today I noticed that gnome-terminal wouldn't open. I have recently compiled and installed Fluxbox and thought maybe it was the culprit. So I restarted X and went into Gnome. Gnome would not load, it would just stay at a black screed. I tried restarting numerous times, and now even when I boot into Fluxbox it is super slow and sometimes things won't load.

Any ideas?

---

### Post by tamoneya on 2008-08-07
drop into the root shell through recovery mode and then run this:```
apt-get install ubuntu-desktop
dpkg-reconfigure ubuntu-desktop
```

---

### Post by stealth17 on 2008-08-08
> **tamoneya said:**
> drop into the root shell through recovery mode and then run this:```
apt-get install ubuntu-desktop
dpkg-reconfigure ubuntu-desktop
```

It did allow me to install Ubuntu-desktop but it didn't fix the problem. Any other ideas?

---

### Post by tamoneya on 2008-08-08
what about ```
/etc/init.d/gdm restart
```Then hit ctrl-alt-F7

---

### Post by stealth17 on 2008-08-08
> **tamoneya said:**
> what about ```
/etc/init.d/gdm restart
```Then hit ctrl-alt-F7

didn't help either I tried reconfiguring gsm and rebooting and it didnt help

---

### Post by tamoneya on 2008-08-08
> **stealth17 said:**
> didn't help either I tried reconfiguring gsm and rebooting and it didnt help

I think you mean gdm.  Anyways lets try this.  It worked on intrepid for me earlier today.```
sudo apt-get remove gdm
sudo apt-get install ubuntu-desktop
```

gdm is a dependcy for ubuntu-desktop so when you uninstall it you lose ubuntu-desktop.  Likewise when you install ubuntu-desktop you reinstall gdm.

---

### Post by stealth17 on 2008-08-08
> **tamoneya said:**
> I think you mean gdm.  Anyways lets try this.  It worked on intrepid for me earlier today.```
sudo apt-get remove gdm
sudo apt-get install ubuntu-desktop
```gdm is a dependcy for ubuntu-desktop so when you uninstall it you lose ubuntu-desktop.  Likewise when you install ubuntu-desktop you reinstall gdm.

Did not help. This is quite frustrating. Looks like I will be doing a fresh install of Ubuntu this puts me back over 3 weeks but I need a working computer.

---

### Post by stealth17 on 2008-08-08
Ended up doing a backup and clean install. The install went great, actually better then before. Maybe it was just meant to be.

---

