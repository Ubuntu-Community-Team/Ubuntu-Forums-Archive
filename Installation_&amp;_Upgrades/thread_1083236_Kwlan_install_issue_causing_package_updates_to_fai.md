---
title: "Kwlan install issue causing package updates to fail"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by bmcsorley on 2009-02-28
Hi,

After having install issues with kwlan I am unable to now remove it and as a result I cannot update my Ubuntu 8.10 build. On running updater it fails and states to run sudo apt-get install -f to fix the issue but this doesn't work. Have searched the forums and tried apt-get remove command as well as dpkg --purge and dpkg -r but none of them work as below.


Description: Ubuntu 8.10
Release: 8.10

kwlan:
  Installed: 0.6.3-1
  Candidate: 0.6.3-1
  Version table:
 *** 0.6.3-1 0
        500 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Packages
        100 /var/lib/dpkg/status


sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  kwlan
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1139kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 227095 files and directories currently installed.)
Removing kwlan ...
gtk-update-icon-cache: Failed to open file /usr/share/icons/hicolor/.icon-theme.cache : File exists
dpkg: error processing kwlan (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 kwlan
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt-get remove kwlan
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  kwlan
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1139kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 227095 files and directories currently installed.)
Removing kwlan ...
gtk-update-icon-cache: Failed to open file /usr/share/icons/hicolor/.icon-theme.cache : File exists
dpkg: error processing kwlan (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 kwlan
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo dpkg --purge kwlan
(Reading database ... 227095 files and directories currently installed.)
Removing kwlan ...
gtk-update-icon-cache: Failed to open file /usr/share/icons/hicolor/.icon-theme.cache : File exists
dpkg: error processing kwlan (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 kwlan

sudo dpkg -r kwlan
(Reading database ... 227095 files and directories currently installed.)
Removing kwlan ...
gtk-update-icon-cache: Failed to open file /usr/share/icons/hicolor/.icon-theme.cache : File exists
dpkg: error processing kwlan (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 kwlan

ProblemType: Package
Architecture: i386
DistroRelease: Ubuntu 8.10
ErrorMessage: subprocess post-removal script returned error exit status 1
NonfreeKernelModules: nvidia
Package: kwlan 0.6.3-1
SourcePackage: kwlan
Title: package kwlan 0.6.3-1 failed to install/upgrade: subprocess post-removal script returned error exit status 1
Uname: Linux 2.6.27-9-generic i686

---

### Post by Partyboi2 on 2009-03-01
Have you tried moving the problem file out of the way?
```
sudo mv /usr/share/icons/hicolor/.icon-theme.cache /usr/share/icons/hicolor/.icon-theme.cache.old 
```
then
```
sudo apt-get -f install
sudo apt-get remove kwlan
```

---

### Post by bmcsorley on 2009-03-04
Hi,

Many thanks for this - worked a treat! My Ubuntu is now upgraded and happy again.

Thanks for your help.

---

