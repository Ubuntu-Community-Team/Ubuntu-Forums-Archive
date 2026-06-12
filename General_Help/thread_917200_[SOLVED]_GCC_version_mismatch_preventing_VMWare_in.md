---
title: "[SOLVED] GCC version mismatch preventing VMWare installation"
date: 2008-09-11
forum: General Help
---

### Post by ztirffritz on 2008-09-11
I'm running Ubuntu 8.04 64. I tried to install the latest version of VMWare (1.07) but it says that there is a mismatch in GCC. The Kernel is compiled using 4.2.3 version but 4.2.4 version is the currently installed version. I tried to force version 4.2.3 using Synaptic, but it doesn't seem to want to regress. The GCC-base seems to be the source of the problem. If I try to force that to the previous version it wants to un-install half of the software on the computer...I don't think that is a good plan. Apparently I accidentally turned on the Hardy Proposed repository and that is how the newer version was installed. Does anyone know how to get around this so that I can get VMWware installed again? It warned me not to do it but I foolishly tried it anyway...now I can't even install the old version. This may not be the correct space to ask this question, so if the mods want to move it feel free.

How do I do a GCC version regression, or how do I recompile the kernel using the current version of GCC that I have?

I originally posted this in the Virtualization section, but later decided that it probably belonged in the general section as the problem probably will affect more than just VMWare.

---

### Post by marcon00 on 2008-09-12
i got the same problem now, after fresh install of ubuntu :\ any suggestions ?

---

### Post by ztirffritz on 2008-09-12
I found that I was able to compile using the different version of GCC without any problems.  I had forgotten to finish the installation process per the sticky in the 'Virtualization' section.  That was why VMWare would not start.  It didn't have anything to do with GCC.  
The GCC mismatch might be a problem later, but as of now, there is nothing that I can do about it without gutting my computer.  What bothers me is that there is no way to turn off Proposed updates.  There will ALWAYS be something that can not be downgraded because it will break something else.  I think that before a user can turn on the 'Proposed' source, it should warn the user with a 2x4 that you can't go backwards, or unselect proposed without causing massive damage to your installation.

---

### Post by fsmithred on 2008-09-12
Look in /var/cache/apt/archives/ and see if you have a .deb file for the older version. Use dpkg to install it (e.g. sudo dpkg -i filename.deb). Or, you can download it here: [http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages) 
Warning: I don't know if it'll want more packages changed or not.

Try 'ls -l /usr/bin/gcc*' to see if you have more than one version there. If you do, you can set the compiler flags to the older version, (something like 'export CC=/usr/bin/gcc-4.2.3') but I have a feeling you'll just find gcc-4.2 only. 

To turn off hardy-proposed, go into Synaptic, Settings, Repositories, click on the Updates tab, and un-check hardy-proposed and/or hardy-backports. Then Reload.

---

### Post by marcon00 on 2008-09-12
i got gcc-4.2 only, i reinstalled from deb package 4.2.3 but it still sees it as 4.2.4 !!

---

### Post by marcon00 on 2008-09-12
was esier to format pc ..

---

### Post by tyk on 2008-10-23
found that compiling with the newer gcc 4.2.4 works fine..

---

### Post by IbnKuldun on 2008-10-30
I did an automated upgrade and it basically ballsed up everything.

My net connection won't work and neither my shared folder. Anyway, i reinstalled VMTools and I get the same problem.

None of the above work for me. If I go ahead with gcc 4.2.4 i get an error when it tries to install vmhgfs.

---

### Post by sgla1 on 2008-11-15
> **tyk said:**
> found that compiling with the newer gcc 4.2.4 works fine..

I can confirm that compiling with gcc 4.2.4 works perfectly on 8.04.

 uname -a
Linux t61p 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux

---

### Post by Floppyjoe on 2008-11-15
> **sgla1 said:**
> I can confirm that compiling with gcc 4.2.4 works perfectly on 8.04.

 uname -a
Linux t61p 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux

I can confirm that compiling with gcc 4.2.4 does not work on 8.04
It compiles but does not run.

---

