---
title: "[SOLVED] Apt-get trouble."
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by RubenK on 2009-01-04
Dear people, ive tried to downgrade from kde4.1 to 3.5. But something went very wrong. At each install i get an error. See for yourself:
```
ruben@ruben-desktop:~$ sudo apt-get install wine
Reading package lists... Done                   
Building dependency tree                        
Reading state information... Done               
The following extra packages will be installed: 
  binfmt-support winbind wine-gecko             
The following packages will be REMOVED:         
  kio-umountwrapper-kde3                        
The following NEW packages will be installed:   
  binfmt-support winbind wine wine-gecko        
0 upgraded, 4 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.                             
Need to get 16.2MB of archives.                               
After this operation, 70.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y                                   
Get:1 http://us.archive.ubuntu.com intrepid/main binfmt-support 1.2.11 [21.4kB]
Get:2 http://us.archive.ubuntu.com intrepid/universe wine 1.0.1-0ubuntu2 [7506kB]
Get:3 http://us.archive.ubuntu.com intrepid/multiverse wine-gecko 0.1.0-0ubuntu1 [5744kB]                                                                                     
Get:4 http://us.archive.ubuntu.com intrepid-updates/main winbind 2:3.2.3-1ubuntu3.3 [2975kB]
Fetched 16.2MB in 1min3s (256kB/s)
(Reading database ... 170548 files and directories currently installed.)
Removing kio-umountwrapper-kde3 ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper'
  found `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop to /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper-kde3'
dpkg: error processing kio-umountwrapper-kde3 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper-kde3
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

There's nothing to find on the net, what is going on here?

I thank you greatly in advance.

---

### Post by RubenK on 2009-01-04
[This](http://ubuntuforums.org/showthread.php?p=4786808) did the trick. Weird, i though i would have found it with google, turns out you always have to do an internal search here on ubuntuforums.org.

---

