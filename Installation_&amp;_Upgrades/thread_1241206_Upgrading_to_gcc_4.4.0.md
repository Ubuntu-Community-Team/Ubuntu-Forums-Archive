---
title: "Upgrading to gcc 4.4.0"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by dgohn on 2009-08-15
I am having problems upgrading to GCC 4.4.0

When I sudo apt-get install gcc this is what I get:

[B]:~# sudo apt-get install gcc
Reading package lists... Done
Building dependency tree
Reading state information... Done
gcc is already the newest version.
[/B]

But its not...

[B]:~# dpkg --list | grep gcc
ii  gcc                                  4:4.3.1-1ubuntu2                        The GNU C compiler
ii  gcc-4.3                              4.3.2-1ubuntu12                         The GNU C compiler
ii  gcc-4.3-base                         4.3.2-1ubuntu12                         The GNU Compiler Collection (base package)
ii  libgcc1                              1:4.3.2-1ubuntu12                       GCC support library


[/B]Can anyone point me in the right direction?

Thanks,

Dan

---

### Post by dgohn on 2009-08-16
*bump*  still having problems, can't figure out how to upgrade to gcc 4.4.0 on Ubuntu Server

---

### Post by PmDematagoda on 2009-08-16
If you want to upgrade GCC, then you will have to upgrade to a version of Ubuntu that has it like Ubuntu Karmic, which unfortunately is still under development, since you will only get security updates(mostly) on a stable version of Ubuntu. 

You could download the GCC source and install it manually, but doing so would be a complicated process since you probably need to recompile all the programs which would take a really long time, there maybe a way to maintain an install of GCC 4.4.0 separately from that provided by Ubuntu, but I do not know of such a way.

Edit:- Perhaps this might help, but do this at your own risk:-
[http://gcc.gnu.org/install/](http://gcc.gnu.org/install/)

---

### Post by dgohn on 2009-08-16
So there is no way to get GCC 4.4.0 onto Ubuntu?  Seems there would be an upgrade or something... odd.

---

### Post by konqui on 2009-08-16
Go in software sources
Under updates tab enable pre and unsupported
Then in terminal
sudo apt-get update
sudo apt-get upgrade gcc

---

### Post by dgohn on 2009-08-16
> **konqui said:**
> Go in software sources
Under updates tab enable pre and unsupported
Then in terminal
sudo apt-get update
sudo apt-get upgrade gcc

Is there a way to do this all from the terminal?

Thanks,

Dan

---

### Post by dgohn on 2009-08-16
Ok did that, but sudo apt-get upgrade gcc is coming back with this...

The following packages will be upgraded:
  gtk2-engines-pixbuf libclamav5 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libpam-smbpass libparted1.8-9 libsmbclient libwbclient0 linux-libc-dev
  parted samba samba-common samba-doc smbclient smbfs update-manager
  update-manager-core winbind


No GCC... any ideas?

---

