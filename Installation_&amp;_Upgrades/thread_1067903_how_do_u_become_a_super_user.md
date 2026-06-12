---
title: "how do u become a super user?"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Arminius on 2009-02-12
I'm trying to install vmware servor
and it won't install it says
"Please re-run this program as the super user.

Execution aborted."

so how do I run this program as the super user?

---

### Post by Sub101 on 2009-02-12
You would need to run:
```
gksudo
```

from the command line.

---

### Post by JTempelm on 2009-02-12
I use "su" and then I enter my root password, that is after the account is active which I learned how to do on the forum. If you type "whoami" after that into the command line it should say you are root, and thus have all root privledges

---

### Post by JK3mp on 2009-02-12
sub101 beat me too it :(

---

### Post by Arminius on 2009-02-12
I did what u said JTempelm, but it just says "su: Authentication failure"
any ideas? and it is the right password

---

### Post by binbash on 2009-02-12
sudo su -

---

### Post by icp on 2009-02-12
try:
```
sudo
```
example:
```
sudo apt-get install PROGRAMM
```

---

### Post by dstew on 2009-02-12
It is probably a bad idea to activate the root account, as suggested JTempelm. That creates a security hole that allows attacks to use administrative privleges. Better to grant yourself temporary superuser (administrative) privleges with [**sudo**]("https://help.ubuntu.com/community/RootSudo"). If the program you are trying to run has a graphical user interfact, you should use **gksudo**. The **su root** command will only work if the root account has been activated. The command **su** without an argument is just shorthand for su root.

---

### Post by donkyhotay on 2009-02-12
You should use sudo or gksudo, it's actually against forum rules to give information on how to enable the root user. It's assumed that anything you need to do with as root can be done with sudo and the few rare things that require root rather then sudo are so advanced you should know how to enable the root user on your own before attempting them.

//edit: another useful tool if you prefer the GUI over the CLI is nautilus-gksu which is available in the ubuntu repos. It allows you to run a program with gksudo by just right-clicking on the file.

---

