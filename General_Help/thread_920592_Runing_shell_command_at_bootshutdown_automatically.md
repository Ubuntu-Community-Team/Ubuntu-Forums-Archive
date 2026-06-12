---
title: "Runing shell command at boot/shutdown automatically?"
date: 2008-09-15
forum: General Help
---

### Post by razta on 2008-09-15
Hello,
I noticed that Ubuntu keeps a record of what ive typed in the shell. What I want to do is run "history -c" at boot or shutdown automatically. Any one know what the best way to do it is?

---

### Post by Idefix82 on 2008-09-15
I strongly recommend you this two part tutorial. They explain how the activities at shutdown, startup, etc. are managed:
[http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/]("http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/")
and
[http://pthree.org/2008/02/27/managing-services-in-ubuntu-part-ii-managing-runlevels/]("http://pthree.org/2008/02/27/managing-services-in-ubuntu-part-ii-managing-runlevels/")

With this you should be able to include any cleanup scripts into the shutdown routine very easily.

---

