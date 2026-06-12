---
title: "can not repair nano package, I get errors in apt-get and aptitude"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by alpharesearch on 2009-01-14
Something is wrong with the nano package (I have no problem to start nano)... but I also get this error messge when I update the system (all the time)...

Markus

```

markus@markus-desktop-work:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up nano (2.0.7-4) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing nano (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 nano
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

```

markus@markus-desktop-work:~$ sudo apt-get remove nano
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nano
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1757kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 300254 files and directories currently installed.)
Removing nano ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing nano (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 nano
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

markus@markus-desktop-work:~$ sudo aptitude reinstall nano
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
  nano 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up nano (2.0.7-4) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing nano (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 nano
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done


```

---

### Post by taurus on 2009-01-14
Try

```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by alpharesearch on 2009-01-14
This didn't help:

```

markus@markus-desktop-work:~$ sudo dpkg --configure -a
markus@markus-desktop-work:~$ sudo apt-get clean
markus@markus-desktop-work:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nano (2.0.7-4) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing nano (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 nano
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by taurus on 2009-01-14
```
sudo apt-get install -a
```

---

### Post by alpharesearch on 2009-01-14
this didn't work...

```

markus@markus-desktop-work:~$ sudo apt-get install -a
E: Command line option 'a' [from -a] is not known.
markus@markus-desktop-work:~$ sudo apt-get install -a nano
E: Command line option 'a' [from -a] is not known.

```

---

### Post by alpharesearch on 2009-01-15
Is there a way to manually remove nano and to install it again?

---

### Post by chrisme52 on 2009-01-19
I having a similiar problem with mythtv and i can't do anything with adept or apt-get.

really frustrating

---

### Post by alpharesearch on 2009-01-21
Now I have this issue also with libmikmod2-dev:

markus@markus-desktop-work:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up nano (2.0.7-4) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing nano (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libmikmod2-dev (3.1.11-a-6ubuntu3) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing libmikmod2-dev (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 nano
 libmikmod2-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by alpharesearch on 2009-01-23
see:
[https://bugs.launchpad.net/bugs/305505](https://bugs.launchpad.net/bugs/305505)

---

