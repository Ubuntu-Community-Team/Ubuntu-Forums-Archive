---
title: "Synaptic Package Maneger Problem"
date: 2008-11-16
forum: General Help
---

### Post by ChrisB111 on 2008-11-16
The synaptic package manger says I have broken packages and when I click fix broken packages in they menu it marks these packages for removal? Should I do this, these look kinda critical and it just says about removing them.

```
linux-generic will be removed
linux-image-2.6.27-7-generic will be removed
linux-image-generic will be removed
linux-restricted-modules-2.6.27-7-generic will be removed
linux-restricted-modules-generic will be removed
```

Thanks,

Chris

---

### Post by soro2005 on 2008-11-16
Don't do it! Does it say which packages are in the way? You can type
```
sudo aptitude install
```
in a terminal window to get more leverage and a choice of different options to fix the issue. The problem is that, once something's broken, it gets difficult to convince apt that you are still in charge. So don't do anything if you're not sure it's what you want to do. You may wind up without a system.

On a positive note: It seems like you have another kernel sitting there. If not, uninstalling the kernel would probably mean a whole lot more packages to be uninstalled.

---

### Post by plucky on 2008-11-16
Find out what kernel you are using.Open a terminal and post output of ```
uname -a
lsb_release -a
```

Did you try an upgrade to Intrepid that didn't work?

---

### Post by ChrisB111 on 2008-11-16
Yes I use the Update Manger and told it to install all the upgrades but it crashed. I restarted it and it seams to have not done much harm its just the package manger and the sound that seams to have changed.

If it helps I am running ubuntu off a usb stick and this is just for fun so I don't mind taking risks because I can just rebuild it form scratch quite easily using a live cd.

I did what you said and it came back with this.

```
chris@ubuntu:~$ sudo aptitude install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 69 not upgraded.
Need to get 0B/23.4MB of archives. After unpacking 0B will be used.
Writing extended state information... Done
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.14_i386.deb
debconf: apt-extracttemplates failed: Bad file descriptor
dpkg-deb: `/var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.14_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.14_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information    
Initializing package states... Done

```

```
chris@ubuntu:~$ uname -a
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
```

```
chris@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
chris@ubuntu:~$ 
```

---

### Post by mgol on 2008-11-16
Maybe try:
```
sudo apt-get -f install
```
It looks for problems and tries to repair it. If there are any packages which are not updated then, type:
```
sudo aptitude update && sudo aptitude dist-upgrade
```
It will then offer You some solutions to the problem.

---

