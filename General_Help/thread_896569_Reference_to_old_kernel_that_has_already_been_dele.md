---
title: "Reference to old kernel that has already been deleted in apt-get"
date: 2008-08-21
forum: General Help
---

### Post by jonolumb on 2008-08-21
I recently tried to install uswsusp using apt-get for better suspend/hibernate performance on my laptop. After entering the install command I get the following errors:

```
jonolumb@jonoxps:~$ sudo apt-get install uswsusp
[sudo] password for jonolumb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxml-libxml-common-perl libcrypt-ssleay-perl libxml-namespacesupport-perl
  libgtk2-trayicon-perl libxml-libxml-perl libcrypt-blowfish-perl
  libxml-sax-perl libxml-simple-perl libfreezethaw-perl
Use 'apt-get autoremove' to remove them.
Suggested packages:
  splashy
The following NEW packages will be installed:
  uswsusp
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/140kB of archives.
After this operation, 422kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package uswsusp.
(Reading database ... 138472 files and directories currently installed.)
Unpacking uswsusp (from .../uswsusp_0.6~cvs20070618-1ubuntu2_i386.deb) ...
Setting up uswsusp (0.6~cvs20070618-1ubuntu2) ...
update-initramfs: Generating /boot/initrd.img-2.6.24.3-tuxonice
Cannot find /lib/modules/2.6.24.3-tuxonice
update-initramfs: failed for /boot/initrd.img-2.6.24.3-tuxonice
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
cryptsetup: WARNING: found more than one resume device candidate:
                     /dev/sda8
                     UUID=cd476ce5-d525-488d-b942-b3eb5280abdc
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
cryptsetup: WARNING: found more than one resume device candidate:
                     /dev/sda8
                     UUID=cd476ce5-d525-488d-b942-b3eb5280abdc
```

The kernel "2.6.24.3-tuxonice" is a custom kernel that I built and installed a while ago. I subsequently uninstalled that kernel using Synaptic but for some reason Ubuntu still seems to think that this kernel is present on the system. Is there any way to get rid of this old kernel for good?

---

### Post by Thingymebob on 2008-08-21
check whats in /boot there'll be some leftovers from your tuxonice build. I guess synaptic just removed the headers from /usr/src and left everything you built in /boot.

leave alone:
abi-2.6.24-19-generic
initrd-2.6.24-19-generic
initrd-2.6.24-19-generic.bak
config-2.6.24-19-generic
System.map-2.6.24-19-generic
vmlinuz-2.6.24-19-generic
memtest86+.bin

as these are your current running kernel
you'll probably want to do a **sudo update-grub** when you're done

---

