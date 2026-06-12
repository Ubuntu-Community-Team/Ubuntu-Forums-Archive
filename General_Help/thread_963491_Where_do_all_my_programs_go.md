---
title: "Where do all my programs go?"
date: 2008-10-30
forum: General Help
---

### Post by strongfan on 2008-10-30
I just went [here]("http://linuxappfinder.com/package/recordmydesktop) to install this package, but I can't seem to find where it gets installed to so I can run it.
Windows has a directory called "C:/Program Files" where all the programs are stored.  Does ubuntu have one of those?  I could have sworn I saw a directory like that somewhere, but I can't seem to find it.

---

### Post by Titan8990 on 2008-10-30
Typically actual programs are stored somewhere in the /usr directory. Looking through it is an inefficient way for a find a program.

Instead use the whereis command.

For example, if I just installed openoffice.org I could find it using the whereis command:

jordan@einstein:~$ whereis openoffice.org
openoffice: /usr/bin/openoffice /etc/openoffice /usr/lib/openoffice /usr/share/openoffice /usr/share/man/man1/openoffice.1.gz

---

### Post by bodhi.zazen on 2008-10-30
Getting to know the file system is always a challenge with a new OS.

First Linux does not use C:\ or D:\ to refer to partitions. 

See: [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

Second, start here :

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by meindian523 on 2008-10-30
And if you wish to find the executable,the which command is more precise.eg:```
easwarh@l1nuxr0cks:~$ which exaile
/usr/bin/exaile
easwarh@l1nuxr0cks:~$ 

```
whereas```
easwarh@l1nuxr0cks:~$ whereis exaile
exaile: /usr/bin/exaile /usr/lib/exaile /usr/share/exaile /usr/share/man/man1/exaile.1.gz
easwarh@l1nuxr0cks:~$ 

```

---

### Post by oldos2er on 2008-10-30
Usually if you type the name of the program or package into a terminal, it will start.

 You can use Synaptic Package Manager to show where each file in a package is installed. Click Status, Installed, right-click on a package, Properties, Installed Files.

---

