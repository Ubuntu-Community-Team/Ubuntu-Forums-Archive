---
title: "upgrading not upgraded packages"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by pyrosrockthisworld on 2009-08-10
just ran ```
apt-get upgrade
``` and got back: ```
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  app-install-data-commercial firefox firefox-3.0 firefox-3.0-branding flashplugin-installer
  language-pack-en language-pack-gnome-en libnspr4-0d libnss3-1d linux-libc-dev
  linux-restricted-modules-common xulrunner-1.9
12 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```just wondering if there is a way to force the upgrade or if there is a good reason not to upgrade the packages?

---

### Post by snowpine on 2009-08-10
sudo apt-get dist-upgrade

---

