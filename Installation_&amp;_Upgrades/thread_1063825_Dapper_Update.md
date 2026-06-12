---
title: "Dapper Update"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by simple66 on 2009-02-08
Hi,

Newbie here, so please be gentle

I am trying to update Ubuntu 6.06 Dapper to 8.04 or above and am running into problem.

So far, I have successfully done
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade

sudo aptitude install update-manager-core

But when trying to
sudo do-release-upgrade -d

I get this error

dpkg: regarding .../libgnome-desktop-2_1%3a2.22.3-0ubuntu1_i386.deb containing libgnome-desktop-2:
 libgnome-desktop-2 breaks gnome-control-center (<< 1:2.22.0-0ubuntu6)
  gnome-control-center (version 1:2.14.2-0ubuntu1) is present and installed.
dpkg: error processing /var/cache/apt/archives/libgnome-desktop-2_1%3a2.22.3-0ubuntu1_i386.deb (--unpack):
 installing libgnome-desktop-2 would break gnome-control-center, and
 deconfiguration is not permitted (--auto-deconfigure might help)
Errors were encountered while processing:
 /var/cache/apt/archives/libgnome-desktop-2_1%3a2.22.3-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have tried several time to do
apt-get -f install
But the same error come back.

Help will be really appreciated

---

### Post by simple66 on 2009-02-08
anybody?

---

### Post by Pumalite on 2009-02-08
Try:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
```

---

