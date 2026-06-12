---
title: "Heron to Ibex upgrade failed twice!"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by DaveHartburn on 2009-01-08
Is the Ubuntu upgrade script broken? Yesterday I upgraded my desktop (Compusys 2Ghz Intel Core Duo), just using the Update Manager GUI. Rather surprisingly towards the end it rebooted my PC without warning or prompt.

On reboot, all was not well. At the GDM login prompt, the mouse and keyboard would not work, though I could do a CTRL-ALT-F6 for a text console. Trying recovery mode it suggested I run 'dpkg --configure -a' manually.

Trying this give a lot of errors. It looks like the system was only half upgraded. Right at the top was the message:
```
The home dir /var/run/dbus you specified can't be accessed: No such file or directory
```

This was quickly fixed with:
```
sudo mkdir /var/run/dbus
sudo dpkg --configure -a
sudo apt-get dist-upgrade
```

The last line was just for good measure and did not pull in any more packages.

This sorted out the problem, so I braved it on my laptop (Toshiba Sat Pro A300). Again I got a sudden reboot followed by a Kernel panic:
```
Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)
```

On booting the older kernel, I got the same errors as my PC and were fixed manually in the same way.

On the plus side, the upgrade fixed graphic card issues on my desktop and the wireless card is recognised on my laptop.

Hopefully this will help other people with the same problem.

---

