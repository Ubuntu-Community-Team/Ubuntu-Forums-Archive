---
title: "Which software is available?"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by hello_from_russia! on 2009-03-21
Hi! I have some repository, can anybody answer me how can I look which software is available to install from it? Thanks!

---

### Post by taurus on 2009-03-21
Look in System -> Add/Remove.

---

### Post by hello_from_russia! on 2009-03-21
Ok, so what I must choose in the list "Show"? There're "All available applications", "All open sources applications", "Canonical-maintainted applications", "Third party applications"...

---

### Post by ami_nakata on 2009-03-21
Hello from USA -

I don't know if this is what you need, but it may help:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)

- cheers, 

Ami

---

### Post by Cruncher on 2009-03-21
What exactly do you mean by "I have some repository"?
With the System->Add/Remove utility you can select and install all packages that are available.
If you have a non-standard repository already added to /etc/apt/sources.list (or via System->SoftwareSources), then packages contained in there will show up in the Add/Remove utility once you updated the database with:
sudo apt-get update
The packages contained within a particular repository are listed in /var/lib/apt/lists in the ...*Packages-Files. For a particular site, you can find which packages are contained there using the grep command, for example:
grep Package: archive.canonical.com*Packages
grep Package: archive.ubuntu.com*main*Packages
and so on.

---

### Post by zvacet on 2009-03-21
@ **hello_from_russia!**

If you want to know whitch packages are available from some repo go to the synaptic and click on sources and after thae pick one you are interested in and all packages from that repo will be listed.

---

