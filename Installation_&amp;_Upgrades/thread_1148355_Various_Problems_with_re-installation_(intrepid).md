---
title: "Various Problems with re-installation (intrepid)"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by OxentroT on 2009-05-04
I've have decided to re-install onto my T40 due to some major issues. However, I have, from a separate computer, formatted a 2GB Kingston data-stick for fat-32 then applied the needed software from the ubuntu live cd using the provided option, as the cdrom drv on my thinkpad is no longer functional. After a successful installation everything seems to run smoothly aside from a few "broken packages" and buffer short-read errors.

I have found and rid myself of these broken pkgs through the means of custom filter and then restart for I can run [sudo apt-get install update] It seemed to finally carry out sans E: errors :) I then proceeded to toggle the icon indicating 4 avail. updates and swiftly got wind of an input/output error through a terminal panel en prompt.



__________________________________________________________________________
eg.a
E: /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.31_i386.deb: short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.27-11-generic/kernel/crypto/cbc.ko')
__________________________________________________________________________

__________________________________________________________________________
eg.b
E: linux-restricted-modules-2.6.27-11-generic: subprocess post-removal script returned error exit status 1
__________________________________________________________________________

__________________________________________________________________________
eg.c
E: /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.31_i386.deb: short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.27-11-generic/kernel/crypto/cbc.ko')
E: /var/cache/apt/archives/evolution-common_2.24.3-0ubuntu1_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/gnome/help/evolution/cs/figures/evo_timezone_a.png')
E: /var/cache/apt/archives/libgphoto2-2_2.4.2-0ubuntu3_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libgphoto2/2.4.2/mustek.so')
E: /var/cache/apt/archives/rhythmbox_0.11.6svn20081008-0ubuntu4.3_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/gnome/help/rhythmbox/fr/figures/rb-notification-window.png')
__________________________________________________________________________




The following result is what happens when I try downloading manually(i assume these were pertaining to the broken pkgs)

__________________________________________________________________________
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
clyde@sleightor:~$ 
clyde@sleightor:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
_________________________________________________________________________




after switching to root:



_________________________________________________________________________
root@sleightor:/home/clyde# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  evolution-common linux-image-2.6.27-11-generic
Suggested packages:
  fdutils linux-doc-2.6.27 linux-source-2.6.27
The following NEW packages will be installed:
  linux-image-2.6.27-11-generic
The following packages will be upgraded:
  evolution-common
1 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
6 not fully installed or removed.
Need to get 0B/40.3MB of archives.
After this operation, 94.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 112820 files and directories currently installed.)
Unpacking linux-image-2.6.27-11-generic (from .../linux-image-2.6.27-11-generic_2.6.27-11.31_i386.deb) ...
Done.
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.31_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.27-11-generic/kernel/crypto/cbc.ko')
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace evolution-common 2.24.1-0ubuntu2 (using .../evolution-common_2.24.3-0ubuntu1_all.deb) ...
Unpacking replacement evolution-common ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/evolution-common_2.24.3-0ubuntu1_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/gnome/help/evolution/cs/figures/evo_timezone_a.png')
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.31_i386.deb
 /var/cache/apt/archives/evolution-common_2.24.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
__________________________________________________________________________

Any and all advice on this issue(s) will be greatly appreciated. 

Thank you in advance.

---

