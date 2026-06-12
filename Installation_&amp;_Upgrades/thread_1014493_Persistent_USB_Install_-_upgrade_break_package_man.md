---
title: "Persistent USB Install - upgrade break package management"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by chiefchief on 2008-12-17
I just did a USB install of ubuntu 8.10 to a 4gb flash drive, and when I upgrade my packages it breaks the package management.  This is the second time this happened.  Last time I was sure it was the kernel upgrade that I installed that did me in.  This time I was careful to avoid any kernel upgrade, but I've still ended up with the following error:

```
Errors were encountered while processing:
 linux-image-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This error pops up when I try to install anything.  Any help would be greatly appreciated.

---

### Post by chiefchief on 2008-12-21
*bump*  I cannot be the only one using a persistent USB that has run into this.

---

### Post by kolage on 2008-12-29
yes, I have the same problem as you, but I also don't know what to do :( . Please, help anyone...

---

### Post by needs2bfree on 2009-01-31
I'm having the same problem. Sorry no new information. Here is what i tried.

ubuntu@ubuntu:~$ sudo dpkg --configure -a
Setting up libc6 (2.8~20080505-0ubuntu8) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ubuntu@ubuntu:~$ sudo dpkg --configure -a
Setting up libc6 (2.8~20080505-0ubuntu8) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135
ubuntu@ubuntu:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ubuntu@ubuntu:~$ 
I couldnt find another thread that discusses the same prolem. If someone can point the way, id be really grateful.

---

