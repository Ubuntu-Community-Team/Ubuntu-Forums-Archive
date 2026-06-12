---
title: "Experimental compiz plugins"
date: 2008-08-17
forum: General Help
---

### Post by phil13 on 2008-08-17
Hi, you probably get dozens of people asking about this but I'm trying to install experimental plugins - atlantis2 in particular. I've tried this guide:
[http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/](http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/)

with no success, though I do now have the latest version of compiz.

I'm running Hardy Heron - installed it via wubi yesterday and loving it...but there's always more wanted!

Any ideas on how I can solve this problem?
Thanks in advance :D

---

### Post by Genius314 on 2008-08-17
[http://forum.compiz-fusion.org/showthread.php?t=8214](http://forum.compiz-fusion.org/showthread.php?t=8214)

That should give you all the information you need to compile additional plugins. Pretty much all you need to do is copy-and-paste.

---

### Post by phil13 on 2008-08-18
I get errors during the process, I think with installing compiz-bcop. There were other errors than this one but I'm assuming that they were as a result of compiz-bcop not installing. This was the code I got with the first terminal command:

phil@phil-laptop:~$ sudo apt-get install compiz-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-dev is already the newest version.
compizconfig-settings-manager is already the newest version.
build-essential is already the newest version.
libtool is already the newest version.
libtool set to manually installed.
libglu1-mesa-dev is already the newest version.
libxss-dev is already the newest version.
libcairo2-dev is already the newest version.
git-core is already the newest version.
The following NEW packages will be installed
  compiz-bcop
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
54 not fully installed or removed.
Need to get 0B/9596B of archives.
After this operation, 127kB of additional disk space will be used.
(Reading database ... 133666 files and directories currently installed.)
Unpacking compiz-bcop (from .../compiz-bcop_0.7.4-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-bcop_0.7.4-0ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/bin/bcop', which is also in package compiz-fusion-bcop
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-bcop_0.7.4-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
phil@phil-laptop:~$ 

how might I get round this issue? In my home folder I now have a 'compiz' folder with lots of plugins in it. I assume these have downloaded correctly and that it is bcop that's the problem.

Thanks

---

### Post by michaelrg1231 on 2008-09-05
this was the error i recieved trying to copy and past to terminal from [http://forum.compiz-fusion.org/showthread.php?t=8214]("http://http://forum.compiz-fusion.org/showthread.php?t=8214") can you help with this issue?



johndoe@johndoe-desktop:~$ sudo apt-get install compiz-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-dev is already the newest version.
compizconfig-settings-manager is already the newest version.
build-essential is already the newest version.
libtool is already the newest version.
libglu1-mesa-dev is already the newest version.
libxss-dev is already the newest version.
libxss-dev set to manually installed.
libcairo2-dev is already the newest version.
libcairo2-dev set to manually installed.
git-core is already the newest version.
The following NEW packages will be installed:
  compiz-bcop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9596B of archives.
After this operation, 127kB of additional disk space will be used.
(Reading database ... 
dpkg: serious warning: files list file for package `scourge-data' missing, assuming package has no files currently installed.
346266 files and directories currently installed.)
Unpacking compiz-bcop (from .../compiz-bcop_0.7.4-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-bcop_0.7.4-0ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/bin/bcop', which is also in package compiz-fusion-bcop
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-bcop_0.7.4-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@mike-desktop:~$

---

### Post by ltemp222 on 2010-06-22
install compiz-fusion-bcop and it will work compiz-bcop is outdated and is no longer in the repo

---

