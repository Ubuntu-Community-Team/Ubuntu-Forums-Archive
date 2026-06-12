---
title: "During the upgrade I get"
date: 2008-11-05
forum: General Help
---

### Post by SanctusMessor on 2008-11-05
I am told it can not install these packages
> 
Could not install nvidia-glx-new

Could not install /var/cache/apt/archives/xserver-xorg-core_2%3a1.5.2-2ubuntu3_amd64.deb

Could not install /var/cache/apt/archives/libhal1_0.5.11-4ubuntu4_amd64.deb

Could not install /var/cache/apt/archives/base-files_4.0.4ubuntu2.2_amd64.deb


There was one more but I accidentally hit the spacebar XD, then I noticed this in the window while its intstalling.

> 
(Reading database ... 104608 files and directories currently installed.)
Removing xserver-xorg-video-via ...
Removing nvidia-glx-new ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx-new (--remove):
 subprocess post-removal script returned error exit status 2
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

and in my last install my xserver was broken by the upgrade, so before I restart this thing what should I do??????

EDIT: at 99% I got "Sorry, the package "xserver-common" failed to install or upgrade.

EDIT2: I cant use adept, "Unable to run the command specified. The file or folder file:///usr/share/applications/kde/adept_installer.desktop does not exist."

---

### Post by arch0njw on 2008-11-08
From a command line (Konsole), try
   *sudo apt-get update; sudo apt-get upgrade*
and see if that clears anything up.  You have something unfinished.  If that works, then try
   *sudo apt-get install nvidia-glx-new*
to see if that will let you reinstall your nvidia drivers.

---

