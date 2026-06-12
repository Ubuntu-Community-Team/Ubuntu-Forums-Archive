---
title: "Ubuntu booted up after install to Terminal mode only"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by black22 on 2009-10-22
I tried to install Ubuntu 8.0.4 multiple times and when it finished up and rebooted without CD I get terminal signon only.
The last lines before server signon are:
>>>>>>>>
*Running local boot scripts (etc/rc.local)
Ubuntu 8.04.3 LTS ubuntu tty1
 
ubuntu login:
>>>>>>>>>>>>>
 
This is new system on MS-7514 with IDE 120 Gb hard drive and IDE CDROM.
Both devices connected to same IDE controller in Cable Select mode. System has Galaxy GeForce 256 video card.

---

### Post by zvacet on 2009-10-23
Type

```
startx
```

or 

```
sudo etc/init.d/gdm start
```

---

