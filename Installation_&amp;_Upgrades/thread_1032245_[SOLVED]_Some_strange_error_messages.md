---
title: "[SOLVED] Some strange error messages"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by MartinDeutschland on 2009-01-06
Hello,
always while installing a package i get this error-message:

> 
E: libghc6-hgl-dev: subprocess pre-removal script returned error exit status 1


Furthermore  i get this message

> 
Errors were encountered while processing:
libghc6-hgl-dev
E: subprocess /usr/bin/dpkg returned an error code (1)


I didn't understand this messages, so i'd asked you for an explanation and how i could fix this problem. Thank you,
Martin

---

### Post by Partyboi2 on 2009-01-06
Can you open  a terminal (Applications>Accessories>Terminal) and try
```
sudo apt-get --reinstall install  libghc6-hgl-dev
``` and post the output back here.

---

### Post by MartinDeutschland on 2009-01-06
Ok, I did it and this is the result:
> 
martin@martin-laptop:~$ sudo apt-get --reinstall install  libghc6-hgl-dev
[sudo] password for martin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libisc32 linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 98 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up libghc6-hgl-dev (3.2.0.0-1) ...
Reading package info from stdin ... done.
ghc-pkg: dependency X11-1.3.0 doesn't exist (use --force to override)
dpkg: error processing libghc6-hgl-dev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libghc6-hgl-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by Partyboi2 on 2009-01-06
Try the workaround mentioned [[COLOR=Blue]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/haskell-hgl/+bug/202974")

---

### Post by MartinDeutschland on 2009-01-07
Thank you very much, everything works fine for me now!

---

