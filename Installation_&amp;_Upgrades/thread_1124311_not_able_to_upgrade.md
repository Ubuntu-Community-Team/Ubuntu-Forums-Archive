---
title: "not able to upgrade"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by rkakkar on 2009-04-13
i'm not able to upgrade from 8.10 to jaunty! 

i typed the following command:

```
$ sudo update-manager -d

```

it flashed the following warning but opened the update manager.

```
Fontconfig error: "~/.fonts.conf", line 1: syntax error

```

i then clicked 'upgrade to 9.04' and then after the screen (see attached screenshot), the update manager simply closes with the following output in the command prompt:

```
extracting 'jaunty.tar.gz'
authenticate 'jaunty.tar.gz' against 'jaunty.tar.gz.gpg' 
Fontconfig error: "~/.fonts.conf", line 1: syntax error

```

what could be the problem?

---

### Post by Aubergines on 2009-04-13
The error message isn't particularly helpful. The fontconfig error probably isn't even anything to do with not being able to update. Have you tried updating from the commandline using this method?

> To upgrade from Ubuntu 8.10 on a server system: install the update-manager-core package if it is not already installed; edit /etc/update-manager/release-upgrades and set Prompt=normal; launch the upgrade tool with the command sudo do-release-upgrade; and follow the on-screen instructions.

I might throw up some more useful messages.

---

