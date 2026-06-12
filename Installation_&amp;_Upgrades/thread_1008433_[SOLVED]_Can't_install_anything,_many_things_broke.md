---
title: "[SOLVED] Can't install anything, many things broken after upgrade to 8.10"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by white_eagle-mk on 2008-12-11
Hi,
    
    I have problems after I upgraded to 8.10 this evening and I can't install nothing **at all!!**
    
    Please help me, here is the terminal output when I try to remove/install something or fix it with install -f
    
   
   UPDATE:
   
   
   After using   [this]("https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/273721/comments/2") solution, mpd works fine again and **it doesn't **segfault anymore, but now I get this when I do sudo apt-get install   
   
   
   ```
whiteeagle@whiteeagle-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnutlsxx13 gnome-bin libwww-ssl0 libgnome32 gnome-libs-data libart2
  libgnorbagtk0 libavformat1d python-configobj python-pyorbit-dev python-bluez
  libwpd-stream8c2a python-qt4-dbus python-libgmail python-daap libgnomeui32
  python-louie libswscale1d python-pylirc libpigment0.3-4
  system-config-printer-common libio-zlib-perl imlib-base liblzo2-dev
  python-coherence liborbit0 gdk-imlib11 libgnomesupport0 gcc-3.3-base
  libwebkitgtk1d libxerces27 libgnorba27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libghc6-hdbc-sqlite3-dev (1.1.4.0.1) ...
Saving old package config file... done.
Writing new package config file... done.
Reading package info from "/usr/lib/haskell-packages/ghc6/lib/HDBC-sqlite3-1.1.4.0/installed-pkg-config" ... done.
ghc-pkg: package HDBC-sqlite3-1.1.4.0 is already installed
dpkg: error processing libghc6-hdbc-sqlite3-dev (--configure):
 subprocess post-installation script returned error exit status 1
Setting up mpd (0.13.2-2ubuntu1) ...
 * Stopping Music Player Daemon mpd                                                                                     [ OK ] 
 * Starting Music Player Daemon mpd                                                                                     [ OK ] 

Errors were encountered while processing:
 libghc6-hdbc-sqlite3-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
whiteeagle@whiteeagle-laptop:~$ sudo dpkg --configure -a

```

---

### Post by cariboo on 2008-12-11
Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages to repair your problem with broken packages.

Jim

---

### Post by white_eagle-mk on 2008-12-11
> **cariboo907 said:**
> Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages to repair your problem with broken packages.

Jim
Doesn't fix the problem, no package gets marked and I still get the same output.

---

### Post by bsmith1051 on 2008-12-11
I'm confused -- is your problem fixed or not?  The title says "[SOLVED}" but I don't see any solution in any of the posts so far.

---

### Post by white_eagle-mk on 2008-12-11
> **bsmith1051 said:**
> I'm confused -- is your problem fixed or not?  The title says "[SOLVED}" but I don't see any solution in any of the posts so far.
Sorry, I forgot to post the solution here, it is solved. You need to add this code to the end of /etc/mpd.conf:


```
audio_output {
*       type "pulse"
*       name "My MPD PulseAudio Output"
}


```

---

