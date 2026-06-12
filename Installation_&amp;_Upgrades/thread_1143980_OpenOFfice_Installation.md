---
title: "OpenOFfice Installation"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by mschraier on 2009-04-30
What procedure so I follow to remove the default OpenOffice in Jaunty so that I can install the version from openoffice.org?

:popcorn:

---

### Post by Pisi-Deff on 2009-04-30
You could instead add the OpenOffice PPA, which contains the newest versions of the program:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main

```
Follow this tutorial to add it: [https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

---

### Post by mschraier on 2009-04-30
ARe they the complete version or the one that is included in Ubuntu?  I would love to totally remove what comes with the install CD and install from their website.

---

### Post by Pisi-Deff on 2009-04-30
As far as I know, they're like the ones included in Ubuntu, sorry :/

Wouldn't it just work to uninstall the openoffice packages via synaptic and then install the original ones?

---

### Post by SuperSonic4 on 2009-04-30
> **Pisi-Deff said:**
> As far as I know, they're like the ones included in Ubuntu, sorry :/

Wouldn't it just work to uninstall the openoffice packages via [s]synaptic[/s] [COLOR="Red"]KPackagekit[/COLOR] and then install the original ones?

```
sudo apt-get remove --purge openoffice
``` from the terminal

---

### Post by mschraier on 2009-04-30
I will give that terminal line a try tonite

---

