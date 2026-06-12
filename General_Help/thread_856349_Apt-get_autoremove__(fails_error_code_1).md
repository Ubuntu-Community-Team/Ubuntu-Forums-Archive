---
title: "Apt-get autoremove  (fails error code 1)"
date: 2008-07-11
forum: General Help
---

### Post by hal8000 on 2008-07-11
After trying to run apt-get autoremove
I receive an error message:

anc@orac:/var/log/apt$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-ubuntu-modules-2.6.24-16-generic
0 upgraded, 0 newly installed, 1 to remove and 18 not upgraded.
1 not fully installed or removed.
After this operation, 15.8MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 125103 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Unfortunately I caused this :(

I manually deleted the oldn old 26.24-16 kernel and modules
using remove. 
I know I should have use apt-get remove packagename

I would imagine there is a log of what apt-get has installed, and apt
is reading this file, which now is a mismatch against my installed software.

Thanks in advance to anyone who can help me with this problem

---

### Post by MasterXandrex on 2008-07-11
You might try

```

sudo apt-get -m autoremove

or

sudo apt-get check

```
 -m is "Attempt to continue if archives are unlocatable"


Xan

---

### Post by hal8000 on 2008-07-11
Thanks for your help, I tried the m option but its still failing

anc@orac:/var/log/apt$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-ubuntu-modules-2.6.24-16-generic
0 upgraded, 0 newly installed, 1 to remove and 18 not upgraded.
1 not fully installed or removed.
After this operation, 15.8MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 125103 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Saw a post somewhere about manually removing an entry from apt-cache or somrthing... just cant remember where it was.

---

### Post by MasterXandrex on 2008-07-11
I think I've got it. Try this

```

sudo apt-get --reinstall install linux-ubuntu-modules-2.6.24-16-generic
and then
sudo apt-get remove linux-ubuntu-modules-2.6.24-16-generic

```


Xan

---

### Post by hal8000 on 2008-07-11
> **UbuntuUser3859 said:**
> I think I've got it. Try this

```

sudo apt-get --reinstall install linux-ubuntu-modules-2.6.24-16-generic
and then
sudo apt-get remove linux-ubuntu-modules-2.6.24-16-generic

```


Xan


In this post Pumalite posted edited /var/lib/dpkg/status
[http://ubuntuforums.org/showthread.php?t=834591](http://ubuntuforums.org/showthread.php?t=834591)

This file keeps a list of all installed packages, and would have worked for me except I made a mess of editing it and didnt back it up :)

Then I tried reinstalling, I'm sure reinstall will also work, but I used
sudo apt-get install linux-ubuntu-modules-2.6.24-16-generic
sudo apt-get remove linux-ubuntu-modules-2.6.24-16-generic
Thanks again for your help

---

