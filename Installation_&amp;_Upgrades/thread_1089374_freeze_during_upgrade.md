---
title: "freeze during upgrade"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by renkinjutsu on 2009-03-07
apt was in the midst of upgrading when my computer froze! .. i had to physically press the power button to turn my computer off... now everytime i try to use apt, i'm returned with this

```
moymoy@moymoy-desktop:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dictionaries-common openoffice.org-base-core openoffice.org-common
  openoffice.org-core openoffice.org-emailmerge openoffice.org-gnome
  openoffice.org-gtk openoffice.org-math openoffice.org-style-human
  openoffice.org-writer python-uno totem
Suggested packages:
  ispell emacsen-common jed-extra openoffice.org-base
  openoffice.org-style-industrial openoffice.org-style-hicontrast
  openoffice.org-evolution openoffice.org-gcj openoffice.org-filter-binfilter
  openoffice.org-java-common openoffice.org-writer2latex totem-plugins-extra
Recommended packages:
  openoffice.org-calc openoffice.org-impress
The following packages will be REMOVED:
  openoffice.org-draw openoffice.org-impress
The following NEW packages will be installed:
  dictionaries-common openoffice.org-base-core openoffice.org-common
  openoffice.org-core openoffice.org-emailmerge openoffice.org-gnome
  openoffice.org-gtk openoffice.org-math openoffice.org-style-human
  openoffice.org-writer python-uno totem ubuntu-desktop
0 upgraded, 13 newly installed, 2 to remove and 15 not upgraded.
4 not fully installed or removed.
Need to get 0B/58.8MB of archives.
After this operation, 180MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Info: dictionaries-common/default-wordlist is already set to
      [american (American English)]. Preserving it.
(Reading database ... 121320 files and directories currently installed.)
Removing openoffice.org-impress ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing openoffice.org-impress (--remove):
 subprocess post-removal script returned error exit status 2
Removing openoffice.org-draw ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing openoffice.org-draw (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 openoffice.org-impress
 openoffice.org-draw
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
how can i fix this? .. any way for me to get apt working again?

---

### Post by Partyboi2 on 2009-03-07
Have you tried running these commands
```
sudo dpkg --configure -a
sudo apt-get -f install
``` to see if it sorts the problem out?

---

### Post by renkinjutsu on 2009-03-07
i've tried doing that.. but both commands returned with the same output..
something was seriously wrong with dpkg.. 

i didn't have many of my own packages installed, so i did a clean reinstall to fix it..

---

### Post by userdce on 2009-03-07
can anybody help in this problem?
i have similar problem
any workaround?

---

