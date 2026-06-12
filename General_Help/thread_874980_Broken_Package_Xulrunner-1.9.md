---
title: "Broken Package Xulrunner-1.9"
date: 2008-07-30
forum: General Help
---

### Post by Nonc on 2008-07-30
Hi

i tried to update a couple of days ago, and this update included xulrunner-1.9 however it encontered an error

```
E: /var/cache/apt/archives/xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb: failed in buffer_write(fd) (10, ret=-1)
```

i have tried these things to no avail

1. fix broken packages via synaptic
2. after seeing that it was needed for firefox, uninstall and reinstall firefox - now i have no firefox (using epiphany instead now) same error
3. sudo apt-get update sudo apt-get install -f
4.

```
sudo apt-get install xulrunner-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgsf-gnome-1-114 guile-1.6 libgoffice-0-common libosp5
  libhtml-tableextract-perl
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  xulrunner-1.9
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7750kB of archives.
After this operation, 28.7kB of additional disk space will be used.
(Reading database ... 150932 files and directories currently installed.)
Preparing to replace xulrunner-1.9 1.9+nobinonly-0ubuntu0.8.04.1 (using .../xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb) ...
Unpacking replacement xulrunner-1.9 ...
dpkg: error processing /var/cache/apt/archives/xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/xulrunner-addons/plugins/libunixprintplugin.so': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


i thought other people might have the same problem, but a few searches turn up similar problems but not the same errors.

Im running Ubuntu 8.04 with everything else updated and firefox 3 was running fine before hand. i have recently suffered a change in internet connection to a much much slower one, so i thought that this might have caused the package to corrupt, but after several attempts, where i think it has downloaded it again each time i think i can rule this theory out.

Does anyone know how to fix this?

Cheers

nonc

cross posted on [http://www.linuxquestions.org/questions/linux-software-2/broken-package-xulrunner-1.9-659157/](http://www.linuxquestions.org/questions/linux-software-2/broken-package-xulrunner-1.9-659157/)

---

### Post by prshah on 2008-07-30
> **Nonc said:**
> 
Unpacking replacement xulrunner-1.9 ...
dpkg: error processing /var/cache/apt/archives/xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/xulrunner-addons/plugins/libunixprintplugin.so': [color=red]No space left on device[/color]


check if you have free disk space with the command ```
df -h
``` if you don't have free space, make some. If you do, post back here with the output of ```
df -i
```

---

