---
title: "Ksysguard calls libavahi-client.so.3: undefined symbol"
date: 2008-08-31
forum: General Help
---

### Post by bogdanbiv on 2008-08-31
I try to start Ksysguard and I get this:
```

bog@bog-desktop:~$ ksysguard %U
bog@bog-desktop:~$ QGDict::hashKeyString: Invalid null key
QGDict::hashKeyString: Invalid null key
ksysguard: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol ''.
ksysguard:
ksysguard: symbol lookup error: /usr/lib/libavahi-client.so.3: undefined symbol: dbus_watch_get_unix_fd
[...]

bog@bog-desktop:~$ ksysguard
bog@bog-desktop:~$ ksysguard: symbol lookup error: /usr/lib/libavahi-client.so.3: undefined symbol: dbus_watch_get_unix_fd
```

Trying to solve it myself by reinstalling the package:
$ sudo apt-get install -f libavahi-client3 
tells me: "libavahi-client3 is already the newest version."



Context information:
Kubuntu Hardy 8.04, KDE 3.5.9
> bog@bog-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bog@bog-desktop:~$ uname -a
Linux bog-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Please help, I don't know where to get from here.

---

