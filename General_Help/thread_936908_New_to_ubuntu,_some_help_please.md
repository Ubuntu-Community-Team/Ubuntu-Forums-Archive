---
title: "New to ubuntu, some help please?"
date: 2008-10-03
forum: General Help
---

### Post by joesoaps on 2008-10-03
how do you install programs? when i download them they save as an archive thingy, what do i do to install it?

---

### Post by Antar Hydrus on 2008-10-03
Run:

sudo apt-get install <application name> 

from the command line. This will download and install almost any application you can think of from the repositories.

---

### Post by joesoaps on 2008-10-03
ok, thanks :).

---

### Post by grannyw on 2008-10-03
that depends on the archive type.search in google howto installation for the certain type

apt-get command is only for the applications which are in repositories

---

### Post by sayakb on 2008-10-03
Download deb packages from [http://getdeb.net](http://getdeb.net)
Open them via GDebi (default) and install them in order of dependencies.

---

### Post by lisati on 2008-10-03
You might also find it useful to look at the Add/Remove programs menu on the Applications menu

---

### Post by Antar Hydrus on 2008-10-03
> **grannyw said:**
> that depends on the archive type.search in google howto installation for the certain type

apt-get command is only for the applications which are in repositories

This is true, but for someone new to Ubuntu, this may be the easiest way to install an application. Some applications, like webmin, you can download in a .tar.gz format or a .deb format. The installation for these other packages varies with the package.

.deb is probably the easiest of the two and usually only requires you to run the following command:

dpkg -i <package name>.deb

.tar and .tar.gz are a little more confusing but usually these packages come with a readme file that tells how to compile and install the application. Off the top of my head (maybe someone a little more knowledgable than me can explain it or correct me if I'm wrong) I think the untar command is this:

tar -xzvf <archive name>.tar.gz

If I'm wrong, please correct me.

btw: I am using Ubuntu server that has no GUI.

---

