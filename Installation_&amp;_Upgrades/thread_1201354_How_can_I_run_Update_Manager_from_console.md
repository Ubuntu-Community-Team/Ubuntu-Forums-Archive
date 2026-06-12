---
title: "How can I run Update Manager from console"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-07-01
I use Update Manager to update, is it possible to get the same effect from the console ?
to update I only know sudo apt-get update.

---

### Post by fbugnon on 2009-07-01
```
$ apt-get update
or
$ aptitude update
```

will update the data-base, while

```
$ sudo apt-get upgrade
or
$ sudo aptitude upgrade
```

will actually upgrade the software accordingly to your sources.list

---

### Post by Aiman on 2009-07-01
use sudo apt-get upgrade or sudo apt-get dist-upgrade

If a package needs to install or remove new dependencies when being upgraded, it will not be upgraded by the upgrade command. For such an upgrade, it is necessary to use the dist-upgrade command.

make sure you used the update command before using the upgrade commands

---

### Post by colau on 2009-07-01
> **hoboy said:**
> I use Update Manager to update, is it possible to get the same effect from the console ?
to update I only know sudo apt-get update.
Yes.
```

sudo apt-get dist-upgrade
sudo update-manager

```

---

### Post by apos on 2011-10-20
Older thread, but incomplete ;)

For newer releases do in a console window:
```
sudo do-release-upgrade
```

---

### Post by goldentony111 on 2011-10-20
> **apos said:**
> Older thread, but incomplete ;)

For newer releases do in a console window:
```
sudo do-release-upgrade
```

this works for me

thanks

---

### Post by oldos2er on 2011-10-20
Back to sleep. Please don't bump old threads.

---

