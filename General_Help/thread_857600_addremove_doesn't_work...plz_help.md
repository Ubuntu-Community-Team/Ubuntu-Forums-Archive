---
title: "add/remove doesn't work...plz help"
date: 2008-07-12
forum: General Help
---

### Post by mefistofeles666 on 2008-07-12
it happens every time I want to install something, mit gives me this error


for htop
E: /var/cache/apt/archives/htop_0.6.6+svn20070915-1_i386.deb: files list file for package `ekiga' contains empty filename

gor another app
E: /var/cache/apt/archives/libwxbase2.8-0_2.8.7.1-0ubuntu3_i386.deb: files list file for package `ekiga' contains empty filename

and it does for every app...what's going on?

---

### Post by VMC on 2008-07-12
Have you tried clean and autoremove:

```
sudo apt-get clean
sudo apt-get autoremove

```

---

### Post by mefistofeles666 on 2008-07-12
I just did and gave me this

matan@Sakura:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ekiga (2.0.12-0ubuntu2) ...
Warning: /usr/share/gconf/schemas/ekiga.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing ekiga (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ekiga
E: Sub-process /usr/bin/dpkg returned an error code (1)
matan@Sakura:~$

---

### Post by boblemur on 2008-07-13
try reinstall or remove if you dont use it

```
sudo apt-get remove ekiga

# and if u actualy want ekiga then

sudo apt-get install ekiga
```

---

