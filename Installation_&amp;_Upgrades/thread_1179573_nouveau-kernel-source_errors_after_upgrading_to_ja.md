---
title: "nouveau-kernel-source errors after upgrading to jaunty"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by dv8NoirFSq on 2009-06-05
hello ubuntu fans,

I was happy with my Ubuntustudio 8.04 until i wanted to upgrade to Jaunty two days ago.. so.. I did.. I upgraded 8.04 to 8.10 and then directly to 9.04

everything seemed to be working fine, networking, languages, sounds..etc, then I wanted to activate Compiz the usual way, installing nvidia driver "nvidia-glx-180", rebooting, enabling... aa stop here .... i got an error during boot, saying X server failed to load... !!

not to go through stupid details of diagnosis and tweaks i did , i ended up with this error whenever I want to install anything, I don't know if this is a different story or it's related to X server. 

> Error! DKMS tree already contains: nouveau-0.0.11+git20090404
You cannot add the same module/version combo more than once.
dpkg: error processing nouveau-kernel-source (--configure):
 subprocess post-installation script returned error exit status 3
Setting up nvidia-180-kernel-source (180.44-0ubuntu1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 180.44
Doing initial module build

Error! Your kernel source for kernel 2.6.24-24-rt cannot be found at
/lib/modules/2.6.24-24-rt/build or /lib/modules/2.6.24-24-rt/source.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.24-24-rt (i686) first.
Done.

Setting up nvidia-glx-180 (180.44-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nouveau-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)searched the web for 4 hours straight for any patches, solutions or anything, i'm still stuck...
the good thing now that i reverted everything i did before.. but i cannot enable nvidia driver, xserver therfore COMPIZ 

i need guidance of how to repair nouveau-kernel-sources and it's DKMS, i have suspicion that i need to update my boot kernel but I don't have a clue if i should, I'm currently running on "2.6.24-24-rt"

if you need any more information, logs just reply,  i will provide it asap

thanks in advance

---

### Post by dv8NoirFSq on 2009-06-06
Bump

---

