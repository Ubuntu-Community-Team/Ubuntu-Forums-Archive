---
title: "apt-get: segmentation fault"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by Sukhinov on 2009-07-04
I am doing "sudo apt-get install"

Getting lot of segmentation faults and errors number 139!

For example: "Setting up gnome-applets-data (2.26.1-0ubuntu1) ... Segmentation fault"

And so on for other packages...

P.S.: I am new to Linux, just instaled it. In Windows I have no such problems...

---

### Post by earthpigg on 2009-07-04
try this:

```
sudo apt-get clean
```


if that worked, stop reading. if not, please run these two commands and show us the output:

```
cat /etc/apt/sources.list
```
and
```
ls /var/cache/apt/
```

for me, its:

```

ep@ep-9:/$ ls /var/cache/apt/
archives  pkgcache.bin  srcpkgcache.bin
ep@ep-9:/$ 

```


this is what google gave me:

[http://www.linuxforums.org/forum/debian-linux-help/80216-apt-get-segmentation-fault.html](http://www.linuxforums.org/forum/debian-linux-help/80216-apt-get-segmentation-fault.html)


you may want to try 

```
rm /var/cache/apt/*.bin
```

it worked for the dude in the thread linked above, but i dont know wtf it does or why it would fix your problem, so use at your own risk.

---

### Post by Sukhinov on 2009-07-05
"sudo apt-get clean" did not help
"rm /var/cache/apt/*.bin" did not help

```
san@san-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ru.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ru.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ru.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://ru.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ru.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://ru.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ru.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://ru.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ru.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ru.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ru.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ru.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

```
san@san-laptop:~$ ls /var/cache/apt/
archives  pkgcache.bin  srcpkgcache.bin
```

SegFaults started to occur after some apdate, I do not remember exactly.

---

### Post by Sukhinov on 2009-07-05
I managed to fix this!!!

I read error logs and found that most errors come from «Scrollkeeper». I do not know what this application is needed for, but I went to Package Manager, and marked Scrollkeeper «for reinstall».

After reinstalling all segmentation faults are gone!!!

---

### Post by Language on 2009-09-23
> **Sukhinov said:**
> I managed to fix this!!!

I read error logs and found that most errors come from «Scrollkeeper». I do not know what this application is needed for, but I went to Package Manager, and marked Scrollkeeper «for reinstall».

After reinstalling all segmentation faults are gone!!!

Thank you! I had the same thing happen on a new netbook remix install today. I had installed some 3rd party eee tools from a repo, not sure if that contributed to the breakage or not. But your fix worked, reinstalling scrollkeeper fixed me right up!

:KS

---

