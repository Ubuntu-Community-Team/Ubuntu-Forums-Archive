---
title: "Add/Remove, Synaptic not working"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by FlamingChainsaws on 2009-10-04
I'm using Jaunty. When I try to open synaptic package manager or add/remove programs the window shows for a split second and then disappears. When I try to install .deb packages in terminal it ***** up as well. For example:

```
joe@<snip>:~$ sudo dpkg -i /home/joe/Desktop/mixxx-1.7.0-ubuntu-i386.deb 
Selecting previously deselected package mixxx.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `app-install-data': Input/output error

```

I get that regardless of what package I'm trying to install. Help with this is greatly appreciated...

---

### Post by stephana on 2009-10-04
maybe this can help you(check out the post from "gil"):
[https://answers.launchpad.net/ubuntu/+source/dpkg/+question/22587]("https://answers.launchpad.net/ubuntu/+source/dpkg/+question/22587")

---

### Post by FlamingChainsaws on 2009-10-04
UUUUUUURGH...no worky. :confused:

---

### Post by stephana on 2009-10-04
I would just remove the /var/lib/dpkg/info/app-install-data.prerm file, then run apt-get -f install

```
sudo mv /var/lib/dpkg/info/app-install-data.prerm /var/lib/dpkg/info/app-install-data.prerm.old
sudo apt-get -f install
```

---

