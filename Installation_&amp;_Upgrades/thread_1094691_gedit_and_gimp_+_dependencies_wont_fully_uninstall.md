---
title: "gedit and gimp + dependencies wont fully uninstall"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by powerplayground on 2009-03-12
whenever I try to remove gedit and gimp I get this error in synaptic package manager:

> E: gedit: subprocess pre-removal script returned error exit status 1
E: libgimp2.0: subprocess post-removal script returned error exit status 2


The programs wont even launch, and I want to get rid of them or reinstall them.

---

### Post by Partyboi2 on 2009-03-12
Hi, open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo apt-get --reinstall install gedit
```

---

### Post by powerplayground on 2009-03-13
I tried to reinstall gedit:
> 
michael@michael-laptop:~$ sudo apt-get --reinstall install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gedit: Depends: gedit-common (>= 2.25) but it is not going to be installed
         Depends: gedit-common (< 2.26) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
michael@michael-laptop:~$ sudo apt-get -f install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gedit is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gedit: Depends: gedit-common (>= 2.25) but it is not going to be installed
         Depends: gedit-common (< 2.26) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So I obviously need gedit-common.

This is what happens when I try to install gedit-common
> 
michael@michael-laptop:~$ sudo apt-get -f install gedit-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  gedit
The following NEW packages will be installed:
  gedit-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1522kB of archives.
After this operation, 14.2MB of additional disk space will be used.
Selecting previously deselected package gedit-common.
(Reading database ... 134603 files and directories currently installed.)
Unpacking gedit-common (from .../gedit-common_2.25.8-0ubuntu2_all.deb) ...
Processing triggers for man-db ...
Setting up gedit-common (2.25.8-0ubuntu2) ...

Setting up gedit (2.25.8-0ubuntu2) ...
/usr/share/gconf/schemas/gedit-file-browser.schemas:1: parser error : Document is empty

^
/usr/share/gconf/schemas/gedit-file-browser.schemas:1: parser error : Start tag expected, '<' not found

^
/usr/share/gconf/schemas/gedit.schemas:1: parser error : Document is empty

^
/usr/share/gconf/schemas/gedit.schemas:1: parser error : Start tag expected, '<' not found

^
dpkg: error processing gedit (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 gedit
E: Sub-process /usr/bin/dpkg returned an error code (1)


Gimp works great now, so gedit is my only problem >.<

---

### Post by Partyboi2 on 2009-03-13
Try 
```
sudo mv /usr/share/gconf/schemas/gedit-file-browser.schemas /usr/share/gconf/schemas/gedit-file-browser.schemas.old
``````

sudo mv /usr/share/gconf/schemas/gedit.schemas /usr/share/gconf/schemas/gedit.schemas.old
```then
```
sudo apt-get --reinstall install gedit
``` and see if gedit now works, or if you still want to remove it
```
sudo apt-get remove gedit
```

---

### Post by powerplayground on 2009-03-13
I get this error whenever I try to do anything to gedit:

> Warning: /usr/share/gconf/schemas/gedit-file-browser.schemas could not be found.
Warning: /usr/share/gconf/schemas/gedit.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing gedit (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 gedit
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

