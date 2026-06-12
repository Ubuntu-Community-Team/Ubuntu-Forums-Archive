---
title: "Update Manager"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by Inarius03 on 2006-01-14
System>Administration>Update Manager

Problem is: when I click on it, it does nothing. Even after I type in the root password. Does anyone know the command to run this in the terminal?

Running 5.10, in case you need that.

BTW, 1st post, and from what I've been reading, you guys give excellent advice/fixes! :cool:

EDIT: Found the file to run: /usr/bin/update-manager.

---

### Post by Inarius03 on 2006-01-14
In case anyone comes along and maybe runs into the same problem:

I also somehow lost my sudo priveleges. In /etc/sudoers, I wasn't listed at the bottom. It was just root, so I had no priveleges to do anything.

In terminal:

su
(password)

visudo

At the bottom, put yourself in there.

---

