---
title: "Can't apt-get update after clean install of 9.04."
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by goaliefight on 2009-04-24
It just hangs at this step:

```
$ sudo apt-get update
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
47% [Waiting for headers]

```

Also the update manager hangs when trying to install or check for updates.

My network connection is working and I can surf. No firewall blockage or anything and I have tried on 2 different ISP connections.

Help!

---

### Post by Artemis3 on 2009-04-24
Try changing the repository mirror, looks like the servers are overloaded with all people upgrading and such.

---

### Post by alphaone on 2009-09-17
Have you solved?

---

