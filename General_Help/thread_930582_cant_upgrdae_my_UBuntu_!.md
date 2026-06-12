---
title: "cant upgrdae my UBuntu !??"
date: 2008-09-26
forum: General Help
---

### Post by anhvu2875 on 2008-09-26
i run this 
```
sudo apt-get upgrade
```
after that i got this error:

dinhvu2875@dinhvu2875-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
linux-image-2.6.24-19-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.4MB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
linux-image-2.6.24-19-generic
Install these packages without verification [y/N]? y
(Reading database ... 103496 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-19-generic 2.6.24-19.34 (using .../linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-19-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb (--unpack):
unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
/var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dinhvu2875@dinhvu2875-desktop:~$

---

### Post by russlar on 2008-09-26
run these in this order:

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

---

### Post by Sycron on 2008-09-26
Well tell us if works.

---

### Post by Sef on 2008-09-26
If Russlar's idea fails to correct the problem, then do this:

System > Administration > Synaptic Package Manager > Edit > Fix Broken Packages.

Then click reload and retry the update.

---

### Post by Sycron on 2008-09-26
It works ?

---

### Post by TeHana86 on 2008-11-14
Thanks russlar

Found this entry. It helped clear the backlog of uninstallable upgrades. Has not managed to solve the original problem of: 

"unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version"

 which remains. Anyone got any ideas.

---

