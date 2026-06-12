---
title: "apt-get doesn't &quot;get&quot;"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by chugru on 2006-01-29
Hi all...

I'm a very new user and am struggling with **apt-get**.

With **apt-get update** I receive many errors:```
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Ign http://kubuntu.org hoary-updates Release.gpg
Ign http://download.skype.com stable Release.gpg
Hit ftp://metalab.unc.edu sarge Release.gpg
Get:1 ftp://ftp.berlios.de unstable Release.gpg
Get:2 ftp://ftp.nerim.net unstable Release.gpg
Get:3 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://kubuntu.org hoary-updates Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://download.skype.com stable Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Get:4 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Ign http://kubuntu.org hoary-updates/main Packages
Hit ftp://metalab.unc.edu sarge Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Err http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
  404 Not Found
Ign http://download.skype.com stable/non-free Packages
Err http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
  404 Not Found
Err http://kubuntu.org hoary-updates/main Packages
  404 Not Found
Hit http://us.archive.ubuntu.com breezy Release
Err http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
  404 Not Found
Ign ftp://ftp.berlios.de unstable Release.gpg
Hit ftp://metalab.unc.edu sarge/non-free Packages
Hit http://download.skype.com stable/non-free Packages
Ign ftp://ftp.nerim.net unstable Release.gpg
Hit http://us.archive.ubuntu.com breezy-updates Release
Hit http://us.archive.ubuntu.com breezy/main Packages
Get:5 ftp://ftp.berlios.de unstable Release
Get:6 ftp://ftp.nerim.net unstable Release
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Ign ftp://ftp.berlios.de unstable Release
Ign ftp://ftp.nerim.net unstable Release
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Get:7 ftp://ftp.berlios.de unstable/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/main Sources
Get:8 ftp://ftp.nerim.net unstable/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Sources
Ign ftp://ftp.berlios.de unstable/main Packages
Ign ftp://ftp.nerim.net unstable/main Packages
Hit ftp://ftp.berlios.de unstable/main Packages
99% [Packages gzip 0]
gzip: stdin: unexpected end of file
Err ftp://ftp.nerim.net unstable/main Packages
  Sub-process gzip returned an error code (1)
Fetched 2B in 5s (0B/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://kubuntu.org/dists/hoary-updates/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list http://kubuntu.org hoary-updates/main Packages (/var/lib/apt/lists/kubuntu.org_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

This certainly can't be right... Would someone please explain how to clean it up?? :) 

Thanks!

---

### Post by psomas on 2006-01-29
can you post your source.list file?
(/etc/apt/source.list)

---

### Post by riwa on 2006-01-29
I might be wrong (not exaclyt a unix guru ;P) but try:
apt-get clean 
apt-get update
apt-get upgrade

And I think you should be up to date..

---

### Post by Adrian on 2006-01-29
You are using obsolete repositories. This might help you:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by chugru on 2006-01-29
**Adrian wrote:** > You are using obsolete repositories. This might help you:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Updating the repositories list and running **apt-get update** now goes smoothly, except:```
Fetched 4441kB in 2m4s (35.6kB/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead. 
```

I was unsure about removing the section **_Ubuntu Backports Project Mirrors_** from my original list. What exactly is the Ubuntu Backports Project??

Is this a necessary section? If so. how do I update it?

Thanks for helping!!

---

### Post by Adrian on 2006-01-29
> I was unsure about removing the section **_Ubuntu Backports Project Mirrors_** from my original list. What exactly is the Ubuntu Backports Project??

When an Ubuntu version (like Breezy Badger) is released, the programs in the main repositories will stay the same, and will thus not be replaced by newer versions (except for bug and security fixes).

For people who want the absolutely newest software and can't wait a couple of months until the next Ubuntu release, the backports repository exists. There, your can find new versions of selected programs that were released after the current stable Ubuntu release.

> 
Is this a necessary section? If so. how do I update it?

It is not necessary, but you probably want it.
Your problem is that the mirrormax server doesn't work anymore. However, I assume that you are using Breezy Badger since you posted in that section. If that is the case, you can safely remove those faulty mirrormax repositories, since they are for Hoary anyway (and you don't need Hoary backports when running Breezy).

Remove them and add this line instead for a **Breezy** backports repository:
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

---

### Post by chugru on 2006-01-29
**Adrian wrote:**> Remove them and add this line instead for a Breezy backports repository:
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

Many thanks for the explanation and instructions!! 

apt-get seems to be running smoothly now! :-D

---

