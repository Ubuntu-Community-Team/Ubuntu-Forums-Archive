---
title: "Adding program to always boot"
date: 2008-08-25
forum: General Help
---

### Post by Reactor5 on 2008-08-25
I'm setting up a server, but I don't know how to add a program (verlihub in my case) to always run, even if a user isn't logged in. Any hints?

---

### Post by -Zeus- on 2008-08-25
try adding a file containing the command to /etc/init.d then use update-rc.d to register the file.

---

