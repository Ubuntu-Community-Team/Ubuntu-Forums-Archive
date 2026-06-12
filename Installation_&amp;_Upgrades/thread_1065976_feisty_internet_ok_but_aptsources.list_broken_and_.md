---
title: "feisty: internet ok but apt/sources.list broken and cant upgrade"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by dlipa on 2009-02-10
Help!  My problems began when I tried to install mysql-server-5.0 to get rails working on Ubuntu:

```
david@ebx:~$ sudo apt-get install mysql-server-5.0
...
The following packages have unmet dependencies:
  mysql-server-5.0: Depends: mysql-client-5.0 (>= 5.0.38-0ubuntu1.4) but it is not going to be installed
E: Broken packages

david@ebx:~$ sudo apt-get install mysql-client-5.0
...
The following packages have unmet dependencies:
  mysql-client-5.0: Depends: libdbd-mysql-perl (>= 1.2202) but it is not installable
E: Broken packages

david@ebx:~$ sudo apt-get install libdbd-mysql-perl
...
Package libdbd-mysql-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdbd-mysql-perl has no installation candidate

```


Installing with synaptic didn't work either (same error).  After spending a couple hours I couldn't find any workaround -- I scoured the net and trying various copies of sources.list and looked over the forums.  So I then tried to upgrade from Feisty to Gutsy.  The upgrade manager worked for a while and then crashed with the following error:

> A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg) Could not resolve 'medibuntu.sos-sts.com'
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_US.bz2) Could not resolve 'medibuntu.sos-sts.com'
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2) Could not resolve 'medibuntu.sos-sts.com'
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/main-edgy/source/Sources.gz](http://ubuntu.beryl-project.org/dists/edgy/main-edgy/source/Sources.gz) 404 Not Found [IP: 195.114.19.35 80]
Failed to fetch [http://kubuntu.org/packages/kde-latest/dists/feisty/main/binary-i386/Packages.gz](http://kubuntu.org/packages/kde-latest/dists/feisty/main/binary-i386/Packages.gz) 301 Moved Permanently
Failed to fetch [http://kubuntu.org/packages/kde-latest/dists/feisty/main/source/Sources.gz](http://kubuntu.org/packages/kde-latest/dists/feisty/main/source/Sources.gz) 301 Moved Permanently
Failed to fetch [http://kubuntu.org/packages/koffice-latest/dists/feisty/main/binary-i386/Packages.gz](http://kubuntu.org/packages/koffice-latest/dists/feisty/main/binary-i386/Packages.gz) 301 Moved Permanently
Failed to fetch [http://kubuntu.org/packages/koffice-latest/dists/feisty/main/source/Sources.gz](http://kubuntu.org/packages/koffice-latest/dists/feisty/main/source/Sources.gz) 301 Moved Permanently
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/feisty/main/binary-i386/Packages.gz](http://kubuntu.org/packages/amarok-latest/dists/feisty/main/binary-i386/Packages.gz) 301 Moved Permanently
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/feisty/main/source/Sources.gz](http://kubuntu.org/packages/amarok-latest/dists/feisty/main/source/Sources.gz) 301 Moved Permanently
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://media.blutkind.org/xgl/dists/edgy/main-edgy/binary-i386/Packages.gz](http://media.blutkind.org/xgl/dists/edgy/main-edgy/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) Could not resolve 'medibuntu.sos-sts.com'
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) Could not resolve 'medibuntu.sos-sts.com'
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) Could not resolve 'medibuntu.sos-sts.com'
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) Could not resolve 'medibuntu.sos-sts.com'



Using other copies of sources.list that I found online invariably produced the same error.  My Comcast cable Internet connection is working fine (I'm posting this from the computer).

How can I proceed either to fix the update manager or to install mysql successfully?

Thank you,
David


PS,
Here is my sources.list:

> 
# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) feisty-seveas all 

deb-src [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) feisty-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse 

deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

# Kubuntu.org bleeding edge KDE
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) feisty main 

deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) feisty main

# Kubuntu.org bleeding edge Koffice
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) feisty main 

deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) feisty main

# Kubuntu.org bleeding edge amaroK
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) feisty main 

deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) feisty main

# Upstream Wine
# GPG key: 387EE263
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main 

deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

# Upstream Opera
# GPG key: 6A423791
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free 

# Upstream Beryl
# GPG key: ed8a569e
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy 

deb-src [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free 

deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial main 

deb-src [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial main

---

### Post by taurus on 2009-02-10
Feisty has expired and has been moved, [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/).  So, you need to change your repos in /etc/apt/sources.list.

---

### Post by dlipa on 2009-02-10
Thank you, that makes sense -- but what exactly do I change in the repo names?  Is there a sources.list available online that is appropriate for this purpose, or something that explains what changes to make?

---

### Post by taurus on 2009-02-10
Instead of having

```
deb http://in.archive.ubuntu.com/ubuntu feisty main restricted 
```
in your /etc/apt/sources.list, you would change it to 

```
http://old-releases.ubuntu.com/ubuntu feisty main restricted
```

---

