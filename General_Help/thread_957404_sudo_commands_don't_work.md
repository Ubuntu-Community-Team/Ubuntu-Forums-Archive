---
title: "sudo commands don't work"
date: 2008-10-24
forum: General Help
---

### Post by richmelk on 2008-10-24
In trying to install nfs I get this response any idea? 
:confused:
richmelk@richmelk-laptop:~$ sudo apt-get install nfs-kernel-server nfs-common portmap
sudo: unable to resolve host richmelk-laptop
richmelk@richmelk-laptop:~$ sudo gedit newport
sudo: unable to resolve host richmelk-laptop
richmelk@richmelk-laptop:~$ su
Password: 
su: Authentication failure
richmelk@richmelk-laptop:~$

---

### Post by SuperSonic4 on 2008-10-24
Check your internet connection. unable to resolve means either your internet or the server is down

---

### Post by woodenbrick on 2008-10-24
See here for a possible solution:
[http://ubuntuforums.org/showthread.php?t=723361]("http://ubuntuforums.org/showthread.php?t=723361")

---

### Post by oldos2er on 2008-10-24
What does your /etc/hosts file look like?

---

### Post by richmelk on 2008-10-24
Thanks for the input. I wasn't able to follow woddenbricks advise but was able to accomplish the same thing by clicking the host tab under networks and change it there. It works now.

---

