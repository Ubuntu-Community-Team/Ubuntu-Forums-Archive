---
title: "Problem with update..."
date: 2008-07-25
forum: General Help
---

### Post by gwu777 on 2008-07-25
Hi there, a few days ago, I tried running the update on ubuntu. It got stuck, so after a few hours I turned it off and restarted, since I have problem running the updates again. Probably unsurprisingly!

Here is some information if it can help anyone:

#######
sudo apt-get -f install
[sudo] password for computer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  virtualbox-ose-guest-modules-2.6.24-16-386 linux-headers-2.6.24-16-generic
  linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openoffice.org-core sun-java6-bin
The following NEW packages will be installed:
  sun-java6-bin
The following packages will be upgraded:
  openoffice.org-core
1 upgraded, 1 newly installed, 0 to remove and 67 not upgraded.
14 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
masson@S:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

######
computer@S:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  openoffice.org-base: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  openoffice.org-calc: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  openoffice.org-draw: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  openoffice.org-evolution: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  openoffice.org-filter-binfilter: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  openoffice.org-math: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  openoffice.org-officebean: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  openoffice.org-writer: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  python-uno: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2) but 1:2.4.1-1ubuntu1 is installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not installed or
                          ia32-sun-java6-bin (= 6-06-0ubuntu1) but it is not installable
E: Unmet dependencies. Try using -f.

######

If anyone can tell me how to fix these problem so that I can use my updates again and install new packages!

Thank you very much,

gwu777

---

### Post by plucky on 2008-07-25
Have you tried ```
sudo dpkg --configure -a
```

> E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

This usually means you have two package managers open.i.e Synaptic or Add/Remove.

Make sure the package managers are not open and then if the above command doesn't work try the ```
sudo apt-get install -f
``` again.Remember the sun-java install requires you to accept an agreement to install and will not continue until you do so.

Good Luck

---

