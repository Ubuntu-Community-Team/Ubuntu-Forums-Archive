---
title: "Get an Error in Ubuntu Update  -_-"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by PHkung on 2009-07-10
last month i got the update notice i try to install it and from that day i got this messege

[COLOR="Red"]**Could not initialize the package information**[/COLOR]

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/th.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

could anyone help me with this?

---

### Post by Partyboi2 on 2009-07-11
Hi, try removing the file and then re downloading it. Open a terminal (Applications>Accessories>Terminal) and
```
sudo rm /var/lib/apt/lists/th.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
```then
```
sudo apt-get update
```

---

### Post by PHkung on 2009-07-15
awwww...... thankyou so much for your advice really help me. i'm totally newbies in Ubuntu.

now i know onemore command "rm" ok thx!!!!!!

sorry for late reply i to busy to tack a look.

---

