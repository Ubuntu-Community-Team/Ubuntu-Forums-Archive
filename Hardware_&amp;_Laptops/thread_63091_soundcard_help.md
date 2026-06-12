---
title: "soundcard help"
date: 2005-09-06
forum: Hardware &amp; Laptops
---

### Post by mwolfe on 2005-09-06
Alright when i installed ubuntu i had a soundblaster live 5.1 in my computer and it worked just fine for the most part. However after a few months my computer had some problems wiht freezing up and sometimes not booting up. Since that card was old and came out of another computer that died altogether, i thought it might be defective, so i took it out of my comp. 

My motherboard has a build in sound card made by nvidia, nforce. Now since i took out the other card all the freezing problems have gone away.  The problem is that my soundcard does not work on initial boot. About a year and ahalf ago i had fedora on this computer and i had the same exact problem.  I get an error while the computer is starting. Then if i restart my computer the soundcard works. But it never works on initial start, only on restarts.. I could never figure it out. 

This morning I went to the nvidia website and downloaded the driver. I tried to install it following the directions, but i get an error saying:

  No precompiled kernel interface was found to match your kernel; this means
  that the installer will need to compile a new kernel interface.

  ERROR: Unable to find the kernel source tree for the currently running
         kernel.  Please make sure you have installed the kernel source files
         for your kernel; on Red Hat Linux systems, for example, be sure you
         have the 'kernel-source' rpm installed.  If you know the correct
         kernel source files are installed, you may specify the kernel source
         path with the '--kernel-source-path' commandline option.


I tried downloading the kernel source with apt-get but it was for an old kernel. I even downloaded nvidia-kernel-source and that didnt work as well, i still get this error message.

It doesnt look like i'm going to be able to get the real driver installed, does anyone have any suggestions for this?

---

