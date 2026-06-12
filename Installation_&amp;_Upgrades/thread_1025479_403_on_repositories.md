---
title: "403 on repositories"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by rgrig on 2008-12-30
Recently I noticed that Synaptic and Update Manager stopped working properly. It might have happened after I moved to xubuntu from ubuntu.

`Reload' in Synaptic and `check' in Update Manager fail with "403 forbidden". The command "apt-get update" works fine. Synaptic has no proxy configured in Preferences. (/etc/apt/apt.conf seems to say that apt-get doesn't use a proxy either.) Changing the server in Synaptic->Preferences doesn't help.

/etc/apt/sources.list:
```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe

```

/etc/apt/apt.conf:
```
Acquire::http::Proxy "false";
```

---

### Post by rgrig on 2009-08-03
The problem was that Synaptic looks for the proxy setting in the gnome system-wide settings even if you say you want a "direct connection". As far as I can tell the only way to edit those settings once you moved to xubuntu is to use gconftool-2. In particular, in this case you can just unset all the keys in /system/proxy:
```

gconftool-2 -R /system/proxy
gconftool-2 -u /system/proxy/aufoconfig_url
gconftool-2 -u /system/proxy/ftp_host
...

```

---

