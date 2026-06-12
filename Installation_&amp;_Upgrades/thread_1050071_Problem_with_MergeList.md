---
title: "Problem with MergeList"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by pstickar on 2009-01-25
Hi,

after 

sudo dpkg --configure -a
sudo apt-get update

the error appears:

E: Vaya, excedió el número de descripciones que este APT es capaz de manejar.
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid-updates_main_i18n_Translation-es
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.

The file /etc/apt/sources.list is the attachment.

Any help will be very much appreciated!

Best,
p.

---

### Post by lorencillo on 2009-06-22
> **pstickar said:**
> Hi,

after 

sudo dpkg --configure -a
sudo apt-get update

the error appears:

E: Vaya, excedió el número de descripciones que este APT es capaz de manejar.
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid-updates_main_i18n_Translation-es
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.

The file /etc/apt/sources.list is the attachment.

Any help will be very much appreciated!

Best,
p.

Hello I quite the same, which is due?

---

### Post by mahboop on 2009-11-12
I've the same problem too when I open Update Manager
I get this:

```

**Could not initialize the package information**

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, 
E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages, 
E:The package lists or status file could not be parsed or opened.'

```

---

### Post by mahboop on 2009-11-15
up

---

### Post by mahboop on 2009-11-20
any help??

---

### Post by mahboop on 2009-11-20
the problem is solved by:
```

sudo rm /var/lib/apt/lists/* -vf

```

[http://www.linuxforums.org/forum/debian-linux-help/51937-aptitude-problem-problem-mergelist.html]("http://www.linuxforums.org/forum/debian-linux-help/51937-aptitude-problem-problem-mergelist.html")

---

