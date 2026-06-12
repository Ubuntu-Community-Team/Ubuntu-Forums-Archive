---
title: "Installation error"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by agentn2o on 2009-07-12
I have had problems installing any software I get the error mentioned below (here, from the dpkg command but it affects all upgrades, installs, etc...): 

sudo dpkg --configure -a

Setting up linux-restricted-modules-2.6.28-13-generic (2.6.28-13.17) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing linux-restricted-modules-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-13-generic; however:
  Package linux-restricted-modules-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.13.17); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-13-generic
 linux-restricted-modules-generic
 linux-generic


How can I fix this?

---

### Post by earthpigg on 2009-07-12
have you restarted your computer since the most recent updates where downloaded?

if not, go ahead and restart. if that still doesn't fix it,

> sudo apt-get update && sudo apt-get dist-upgrade

has fixed this for me, in the past.

---

### Post by agentn2o on 2009-07-12
Thanks... this problem has plagued me for a month or so and despite multiple restarts, etc...

I tried another tip to just remove and reinstall and it worked! Here's the result:

calvin@susie:~$ sudo apt-get remove linux-restricted-modules-2.6.28-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnotify-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic linux-restricted-modules linux-restricted-modules-2.6.28-13-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 4 to remove and 5 not upgraded.
4 not fully installed or removed.
After this operation, 2519kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 149168 files and directories currently installed.)
Removing linux-generic ...
Removing linux-restricted-modules ...
Removing linux-restricted-modules-generic ...
Removing linux-restricted-modules-2.6.28-13-generic ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing linux-restricted-modules-2.6.28-13-generic (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

calvin@susie:~$ sudo apt-get install linux-restricted-modules-2.6.28-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.28-13-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libnotify-bin
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/829kB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package linux-restricted-modules-2.6.28-13-generic.
(Reading database ... 149102 files and directories currently installed.)
Preparing to replace linux-restricted-modules-2.6.28-13-generic 2.6.28-13.17 (using .../linux-restricted-modules-2.6.28-13-generic_2.6.28-13.17_i386.deb) ...
Unpacking replacement linux-restricted-modules-2.6.28-13-generic ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Setting up linux-restricted-modules-2.6.28-13-generic (2.6.28-13.17) ...
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic


I think this is yet another problem that came about from my unfortunate decision to upgrade to EXT4 ... I get alot of crashes while updates are occurring and I think one happened in the middle of this package download or something.

---

### Post by RJARRRPCGP on 2009-07-12
> **agentn2o said:**
> Thanks... this problem has plagued me for a month or so and despite multiple restarts, etc...

I tried another tip to just remove and reinstall and it worked! Here's the result:

calvin@susie:~$ sudo apt-get remove linux-restricted-modules-2.6.28-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnotify-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic linux-restricted-modules linux-restricted-modules-2.6.28-13-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 4 to remove and 5 not upgraded.
4 not fully installed or removed.
After this operation, 2519kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 149168 files and directories currently installed.)
Removing linux-generic ...
Removing linux-restricted-modules ...
Removing linux-restricted-modules-generic ...
Removing linux-restricted-modules-2.6.28-13-generic ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing linux-restricted-modules-2.6.28-13-generic (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

calvin@susie:~$ sudo apt-get install linux-restricted-modules-2.6.28-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.28-13-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libnotify-bin
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/829kB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package linux-restricted-modules-2.6.28-13-generic.
(Reading database ... 149102 files and directories currently installed.)
Preparing to replace linux-restricted-modules-2.6.28-13-generic 2.6.28-13.17 (using .../linux-restricted-modules-2.6.28-13-generic_2.6.28-13.17_i386.deb) ...
Unpacking replacement linux-restricted-modules-2.6.28-13-generic ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Setting up linux-restricted-modules-2.6.28-13-generic (2.6.28-13.17) ...
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic


I think this is yet another problem that came about from my unfortunate decision to upgrade to EXT4 ... I get alot of crashes while updates are occurring and I think one happened in the middle of this package download or something.

Looks like probably the HDD is corrupted. You should test your motherboard, processor, RAM and HDD. 

You may have unreliable hardware.

You may be required to take some RAM out. Using one of the other RAM slots may be the cause.

Because, I have none of those problems. (even though I did a from scratch installation)

---

### Post by agentn2o on 2009-07-12
Nope it's entirely related to the EXT4 bug... here's the launchpad thread:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824)

It only started once I upgraded to ext4. I just have to be REAL careful when deleting files... but I have no control of file deletion activity when an upgrade is in progress so it frequently crashes while updating.

---

