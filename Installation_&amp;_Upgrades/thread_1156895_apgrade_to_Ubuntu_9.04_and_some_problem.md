---
title: "apgrade to Ubuntu 9.04 and some problem"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by inject0r on 2009-05-12
hi there,

during upgrade from 8.10 to 9.04 from update manager i get these message :

------ message 1------
Could not install '/var/cache/apt/archives/linux-image-2.6.28-11-generic_2.6.28-11.42_i386.deb'

The upgrade will continue but the '/var/cache/apt/archives/linux-image-2.6.28-11-generic_2.6.28-11.42_i386.deb' package may be in a not working state. Please consider submitting a bug report about it.

short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.28-11-generic/kernel/drivers/char/stallion.ko')

------ message 2------
Could not install '/var/cache/apt/archives/libmad0_0.15.1b-4_i386.deb'

The upgrade will continue but the '/var/cache/apt/archives/libmad0_0.15.1b-4_i386.deb' package may be in a not working state. Please consider submitting a bug report about it.
unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/shlibs': Stale NFS file handle

------ message 3------
Could not install 'linux-image-2.6.28-11-generic'

The upgrade will continue but the 'linux-image-2.6.28-11-generic' package may be in a not working state. Please consider submitting a bug report about it.

no package named `linux-image-2.6.28-11-generic' is installed, cannot configure


------ message 4------
Could not install 'libmad0'

The upgrade will continue but the 'libmad0' package may be in a not working state. Please consider submitting a bug report about it.
package libmad0 is not ready for configuration

--------

after finish, it's seems that all is ok but when i want to run any install commands such as apt-get install or upgrade, i receives this output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libmad0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B/74.5kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 140585 files and directories currently installed.)
Preparing to replace libmad0 0.15.1b-3 (using .../libmad0_0.15.1b-4_i386.deb) ...
Unpacking replacement libmad0 ...
dpkg: error processing /var/cache/apt/archives/libmad0_0.15.1b-4_i386.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/shlibs': Stale NFS file handle
Errors were encountered while processing:
 /var/cache/apt/archives/libmad0_0.15.1b-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

i think the main problem is from this error line  
unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/shlibs': Stale NFS file handle

but i don't know how to fix this issue 


any suggestion is welcome

regards,

---

### Post by inject0r on 2009-05-12
still has same problem:(

---

### Post by Partyboi2 on 2009-05-12
Hi, open a terminal and try clearing out the cache
```
sudo apt-get clean
sudo apt-get -f install
sudo apt-get install libmad0

```

---

### Post by inject0r on 2009-05-12
Partyboi2, thnx for replay

i've got the same output

$sudo apt-get clean
$sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mbr libdvdread3 xutils-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmad0
The following packages will be upgraded:
  libmad0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 74.5kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) jaunty/main libmad0 0.15.1b-4 [74.5kB]
Fetched 74.5kB in 3s (24.8kB/s) 
(Reading database ... 140585 files and directories currently installed.)
Preparing to replace libmad0 0.15.1b-3 (using .../libmad0_0.15.1b-4_i386.deb) ...
Unpacking replacement libmad0 ...
dpkg: error processing /var/cache/apt/archives/libmad0_0.15.1b-4_i386.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/shlibs': Stale NFS file handle
Errors were encountered while processing:
 /var/cache/apt/archives/libmad0_0.15.1b-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

also:
 sudo apt-get install libmad0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mbr libdvdread3 xutils-dev
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libmad0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B/74.5kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 140585 files and directories currently installed.)
Preparing to replace libmad0 0.15.1b-3 (using .../libmad0_0.15.1b-4_i386.deb) ...
Unpacking replacement libmad0 ...
dpkg: error processing /var/cache/apt/archives/libmad0_0.15.1b-4_i386.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/shlibs': Stale NFS file handle
Errors were encountered while processing:
 /var/cache/apt/archives/libmad0_0.15.1b-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

as i mentioned above any installation aborted with this error

more help ?

---

### Post by inject0r on 2009-05-12
what does this message refer to :
unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/shlibs': Stale NFS file handle

?

---

### Post by inject0r on 2009-05-12
update..


when i try to update packages through synaptic package manager i get this window "after click on detail":


[IMG]http://img392.imageshack.us/img392/9413/updatemanager.png[/IMG]


as you see here he want to update libmad0 from 0.15.1b-3 to 0.15.1b-4 but as you know it won't due to my previous problem

so i searched for  0.15.1b-3 version and the result is NOTHING 

$locate 0.15.1b-3
-none-

but :
$ locate 0.15.1b-4
/home/user/.local/share/Trash/info/libmad0_0.15.1b-4_i386.deb.trashinfo
/var/cache/apt/archives/libmad0_0.15.1b-4_i386.deb

so i wondering if i can solve my issue by rollback to the old version "0.15.1b-3" so i can reinstall the update again 

any suggestions ?

---

### Post by inject0r on 2009-05-12
up for importance

---

### Post by inject0r on 2009-05-13
anyone know what does this message mean ? 
"unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/shlibs': Stale NFS file handle" ?

---

### Post by inject0r on 2009-05-14
SOLVED :D

just boot from recovery mode, choose command line or something similar then type this magic command
```
fsck
```he will say "there is a bla bla bla in /var/lib/dpkg/tmp.ci/shlibs cash, do u wanna clean it?" directly say Y and wait for a while then all will be ok

--inject0r

---

