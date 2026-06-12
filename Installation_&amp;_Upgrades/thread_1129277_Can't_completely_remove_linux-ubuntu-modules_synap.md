---
title: "Can't completely remove linux-ubuntu-modules synaptic"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by berilthedwarf on 2009-04-18
In synaptic under the "Not Installed (Residual config) status it lists linux-ubuntu-modules-2.6.22-15-generic.  I'm not sure how long ago the package was removed, but I'm using jaunty 2.6.28-11-generic; so probably quite some time ago.

When attempting the compltely remove the package, it fails and the details in the embedded terminal are as follows:

```
(Reading database ... 260835 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-15-generic ...
Purging configuration files for linux-ubuntu-modules-2.6.22-15-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-15-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-15-generic
Cannot find /lib/modules/2.6.22-15-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-15-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-15-generic (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

Any ideas?

---

### Post by zvacet on 2009-04-18
```
sudo apt-get --purge remove linux-ubuntu-modules-2.6.22-15-generic
```

or 

```
sudo dpkg --remove --force-remove-reinstreq linux-ubuntu-modules-2.6.22-15-generic
```

---

### Post by berilthedwarf on 2009-04-18
Thanks for the response, but no dice:

```

$ sudo apt-get --purge remove linux-ubuntu-modules-2.6.22-15-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-ubuntu-modules-2.6.22-15-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ sudo dpkg --remove --force-remove-reinstreq linux-ubuntu-modules-2.6.22-15-genericdpkg - warning: ignoring request to remove linux-ubuntu-modules-2.6.22-15-generic, only the config
 files of which are on the system.  Use --purge to remove them too.

$ sudo dpkg --purge --remove --force-remove-reinstreq linux-ubuntu-modules-2.6.22-15-generic
dpkg: conflicting actions -r (--remove) and -P (--purge)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

$ sudo dpkg --purge --force-remove-reinstreq linux-ubuntu-modules-2.6.22-15-generic
(Reading database ... 260820 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-15-generic ...
Purging configuration files for linux-ubuntu-modules-2.6.22-15-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-15-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-15-generic
Cannot find /lib/modules/2.6.22-15-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-15-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-15-generic (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-15-generic

```

Is apt/dpkg caching some information making it think there's something there that really isn't?

---

### Post by Thuenor on 2009-04-24
I found a working solution at [the french Ubuntu forum]("http://forum.ubuntu-fr.org/viewtopic.php?id=239390"):

[LIST]
Use your editor-of-choice to replace the contents of /var/lib/dpkg/info/linux-ubuntu-modules-2.6.22-15-generic.postrm with:
```
#!/bin/bash
exit 0
```[/LIST]
[LIST]Execute the following command:
```
sudo dpkg --purge linux-ubuntu-modules-2.6.22-15-generic
```[/LIST]

Good luck!

---

### Post by berilthedwarf on 2009-04-24
Sweet!  Success!  That worked perfectly!

---

