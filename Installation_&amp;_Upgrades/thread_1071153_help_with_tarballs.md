---
title: "help with tarballs?"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by coolbeans777 on 2009-02-15
I need help with this, i want to install some programs on ubuntu, but they are all in tar.gz/tgz/tar.bz2 format and i can't figure out how to install them. When i try to install, i do this
1. download the file
2. open terminal and type in "tar xzfv <programname.tar.gz>" (i know that xzfv changes to xjfv when it is tar.bz2, so im pretty sure that isn't my problem.)
3. type in "cd <name of extracted folder>"
4. go in root "sudo su"
5. then i type in "./configure"
after that it tells me "bash: ./configure: No such file or directory"

What am I doing wrong?

---

### Post by Javich on 2009-02-15
Hello coolbeans777, as far as I can tell (for what you wrote) you're not doing anything wrong. In other linux distros (like SuSE) is "mandatory" to have the configure script when distributing software from source code, however in Ubuntu sometimes there is no configure script, so my suggestion is just to type "make" and if it compiles, you should be able to sudo make install. 

Cheers.
Javier

---

### Post by x33a on 2009-02-15
it means that there isn't a configure file present in the folder.

either the archive is missing the configure file, or it installs in some other way.

read the "README"/"INSTALL" files present in the folder.

---

### Post by coolbeans777 on 2009-02-15
I just tried to just type make, and it said "make: *** No files specified and no makefile found. Stop." and i read the readme and still the same thing happened.

---

### Post by x33a on 2009-02-15
can you post a link to the .tar.gz you are trying to install?

---

### Post by coolbeans777 on 2009-02-15
[http://mupen64.emulation64.com/down.htm](http://mupen64.emulation64.com/down.htm)

its the first link on the page

---

### Post by oldos2er on 2009-02-16
Don't run ./configure or make as root; you should only need to run make install as root. This archive contains a .pdf file with installation instructions in the doc directory.

---

### Post by Javich on 2009-02-16
Dude, just get the mupen64 linux tarball (not source), uncompress it and run the executable (./mupen64). That's it.

Cheers,

Javier

---

