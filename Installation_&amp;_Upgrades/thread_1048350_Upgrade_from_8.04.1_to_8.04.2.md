---
title: "Upgrade from 8.04.1 to 8.04.2"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by ProNux on 2009-01-23
Guys,

Ubuntu version 8.04.2 LTS is just recently released.  How can I upgrade my 8.04.1 LTS installation?  I searched the forum but I can't find one.

Do I need to download the new ISO?

Thanks....

---

### Post by snowpine on 2009-01-23
Just run the update manager, or from the terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

8.04.1 and 8.04.2 are just Live CD version numbers; the installed systems are identical as long as all your updates are up to date. :)

---

### Post by OrangeCrate on 2009-01-23
> The Ubuntu team is proud to announce the release of Ubuntu 8.04.2 LTS, the second maintenance update to Ubuntu's 8.04 LTS release. This release includes updated server, desktop, and alternate installation CDs for the i386 and amd64 architectures. **In all, over 200 updates have been integrated, and updated installation media has been provided so that fewer updates will need to be downloaded after installation**...

[http://ubuntuforums.org/showthread.php?t=1047613](http://ubuntuforums.org/showthread.php?t=1047613)

---

### Post by ProNux on 2009-01-23
> **snowpine said:**
> Just run the update manager, or from the terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

8.04.1 and 8.04.2 are just Live CD version numbers; the installed systems are identical as long as all your updates are up to date. :)

Wow thanks for the very quick reply.

I tried the apt-get update and apt-get upgrade but it said...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Might it be that I am updated?

---

### Post by OrangeCrate on 2009-01-23
^,

Your computer is already up to date.

As said, the point releases are just new disks, so that when you download and install, you won't have as many updates to install. .1 or .2 doesn't mean anything unless you want to download a new disk.

---

### Post by taurus on 2009-01-23
```
lsb_release -a
```

---

### Post by ProNux on 2009-01-24
> **taurus said:**
> ```
lsb_release -a
```

Thanks to you guys.  I am on the latest version 8.04.2.

My problem right now is my Ralink RT-73 - based WLAN card (Edimax EW-7318USg) has become unstable.  Internet connection (from an open Hotspot) sometimes disconnects without warning.  Gotta psot this to the Networking forum.

---

