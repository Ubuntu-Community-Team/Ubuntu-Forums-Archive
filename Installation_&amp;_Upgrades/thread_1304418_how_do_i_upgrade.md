---
title: "how do i upgrade?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Catok on 2009-10-29
how do i upgrade from ubuntu 9.04 to 9.10?

---

### Post by dummy910 on 2009-10-29
you can use the terminal:
> sudo do-release-upgrade -d
or use the update manager gui program, 
System>Administration>Update Manager

---

### Post by slakkie on 2009-10-29
> **dummy910 said:**
> you can use the terminal:

or use the update manager gui program, 
System>Administration>Update Manager

That command it to upgrade to development releases mate.

```

# GUI (you might want to use gksude, or whatever the thing is to run gui apps with sudo
sudo update-manager

# cli
sudo aptitude install update-manager-core
sudo do-release-upgrade

```

---

### Post by i.r.id10t on 2009-10-29
Or download the alternate install cd.  Make sure you have all 9.04 updates, then run the upgrade script on the alt cd.

---

### Post by phillw on 2009-10-29
Or, the way i did it was ....

[http://www.ubuntugeek.com/upgrade-ubuntu-9-04-jaunty-jackalope-to-ubuntu-9-10-karmic-koala-beta.html](http://www.ubuntugeek.com/upgrade-ubuntu-9-04-jaunty-jackalope-to-ubuntu-9-10-karmic-koala-beta.html)

just remember about the removing -d  as it says in the instructions !!!!

Phill.

---

