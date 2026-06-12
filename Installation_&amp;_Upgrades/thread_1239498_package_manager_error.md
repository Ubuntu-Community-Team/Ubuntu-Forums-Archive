---
title: "package manager error"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by techrascal on 2009-08-13
the exact error i'm gettin is:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2 No such file or directory), E:The package lists or status file could not be parsed or opened.'




no idea where to start debugging.....
thanx in advance...

---

### Post by Partyboi2 on 2009-08-13
Hi, open a terminal and try[FONT=monospace] replacing your status file with the backup one.
[/FONT]```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broke
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

