---
title: "why such a HUGE folder from kernel compile?"
date: 2008-07-28
forum: General Help
---

### Post by logos34 on 2008-07-28
I just tried several times to test compile a custom kernel from 2.6.26 source, and kept running out of space!  I had to enlarge root several GIGABYTES (!) before it finally worked.  I went the manual route first (from the .bz2), but it kept filling up /.  So I finally thought I try KernelCheck after adding 3 gb space.  It worked, but the resulting folder "linux-2.6.26" is a whopping 2.4 GB. 

Why so large?  I know you can delete it afterward, but is there way to build the kernel from another partition (besides /usr/src)?  I want to do this for my regular install but root is boxed in and can't be expanded.

---

### Post by galileon on 2008-07-28
move the linux.version.blah/ folder from /usr/src to say /home/yournamehere/

ie you naow have /home/yournamehere/linux.version.blah/

then do:

sudo ln -s /home/yournamehere/linux.version.blah/ /usr/src/linux

then cd /usr/src/linux

do_your_stuff_here.

---

### Post by logos34 on 2008-07-28
> **galileon said:**
> move the linux.version.blah/ folder from /usr/src to say /home/yournamehere/

ie you naow have /home/yournamehere/linux.version.blah/

then do:

sudo ln -s /home/yournamehere/linux.version.blah/ /usr/src/linux

then cd /usr/src/linux

do_your_stuff_here.

ah, so that's how you do it.  thanks.  I'll try that.  (you've jogged my memory--now I remember something similar on [this page]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/kernel-baking.html"), but I didn't know whether it could be trusted, it seemed to differ slightly from all the other guides).

---

### Post by logos34 on 2008-07-28
just to verify: I can delete the "linux-2.6.26" folder afterward, can I not?  I won't need it again later for anything, right?

---

### Post by galileon on 2008-07-28
err i think you somehow need *it* or *something inside* with the name of "kernel headers" or something like that, to build modules ie drivers from source if they are not  part of the kernel tree...eg nvidia driver installer from nvidia website would ask for the darn headers...

i don't quite remember though, long time since i compiled linux kernels...

googling "linux 2.6 kernel headers" might help

---

### Post by logos34 on 2008-07-28
I was afraid of that...makes sense, especially the nvidia part (probably needed by envyNG driver install)...if I just knew what exactly to keep, cuz I just don't have the space.  guess I've got a little researching to do

---

### Post by LinuxRocks713 on 2008-07-28
> **logos34 said:**
> just to verify: I can delete the "linux-2.6.26" folder afterward, can I not?  I won't need it again later for anything, right?

Can't you do make clean inside the tree to save space?

---

### Post by logos34 on 2008-07-28
well, as I said I used KernelCheck--I thought it did 'make kpkg-clean'...maybe I missed an option box or something.

---

### Post by LinuxRocks713 on 2008-07-28
> **logos34 said:**
> well, as I said I used KernelCheck--I thought it did 'make kpkg-clean'...maybe I missed an option box or something.

You can try it again yourself:

```

cd /usr/src/linux
make clean
make distclean
make kpkg-clean # I doubt such a target exists in Makefile

```

---

### Post by logos34 on 2008-07-28
I already deleted the folder.  (It was just a trial run)

I'll try it on the next compile today.

---

### Post by logos34 on 2008-07-28
Another question:

Do you know if I need to compile the linux-restricted-modules if I just want to use the nvidia glx-new driver (not the proprietary binary driver)?  I had trouble yesterday with that

i was reading this:

[https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules)
[https://help.ubuntu.com/community/Kernel/Compile#Modify%20the%20source%20for%20your%20needs](https://help.ubuntu.com/community/Kernel/Compile#Modify%20the%20source%20for%20your%20needs)

---

### Post by galileon on 2008-07-28
> **logos34 said:**
> Another question:

Do you know if I need to compile the linux-restricted-modules if I just want to use the nvidia glx-new driver (not the proprietary binary driver)?  I had trouble yesterday with that

i was reading this:

[https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules)
[https://help.ubuntu.com/community/Kernel/Compile#Modify%20the%20source%20for%20your%20needs](https://help.ubuntu.com/community/Kernel/Compile#Modify%20the%20source%20for%20your%20needs)

u could always get just the nvidia binary blob from their website

---

### Post by logos34 on 2008-07-28
you mean this:

[NVIDIA-Linux-x86_64-173.14.05-pkg2.run]("http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run")

and run through  the interactive installation and let it build the headers?  I 've done that before lots of times, but does it work with custom compiled kernel?

Or can't I just grab this source pkg from the intrepid archive:

[linux-restricted-modules_2.6.26-5.11.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules_2.6.26-5.11.tar.gz")

and compile that?  Will that work (I'm using the 'linux-2.6.26' from [TLKA]("http://www.kernel.org/"))

---

### Post by galileon on 2008-07-28
> **logos34 said:**
> you mean this:

[NVIDIA-Linux-x86_64-173.14.05-pkg2.run]("http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run")

and run through  the interactive installation and let it build the headers?  I 've done that before lots of times, but does it work with custom compiled kernel?

Or can't I just grab this source pkg from the intrepid archive:

[linux-restricted-modules_2.6.26-5.11.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules_2.6.26-5.11.tar.gz")

and compile that?  Will that work (I'm using the 'linux-2.6.26' from [TLKA]("http://www.kernel.org/"))

yeah, no reason the former shudnt work with a custom kernel, it might ask you where the source tree lives, so tell it /home/user/wherever_u_stored_it


the second might work too...but it would probably be more of a hassle since it contains other drivers you don't need...

---

### Post by PmDematagoda on 2008-07-29
About the linking of the kernel source to /usr/src/linux, it really is not that necessary as long as you keep the kernel source static(i.e. don't move it anywhere after the compile and install).

---

### Post by sdennie on 2008-07-29
If you are building the kernel using make-kpkg, you can greatly reduce the needed disk space by using:

```

INSTALL_MOD_STRIP=1 fakeroot make-kpkg ... whatever you were going to type ...

```

If you are going to use custom kernels and the nvidia driver, I also highly recommend that you download the driver from the nvidia website and install it using one of the many guides you can find this forum.  Then, if you plan to update your custom kernel, you may want to use this guide to automatically install the nvidia drivers into new kernels: [ HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by logos34 on 2008-07-30
> **vor said:**
> If you are going to use custom kernels and the nvidia driver, I also highly recommend that you download the driver from the nvidia website...

Tell me, Vor, what are my options if I can't use the nvidia driver?  Just use 'vesa'? 

Seems I've hit a royal road bump on my way to a custo kernel...none of the nvidia releases will successfully build a kernel module against the existing 2.6.24 kernel source, let alone a new 2.6.26.  I got EnvyNG to install one on my test x64 hardy installation (used KernelCheck '-Ultimate'), but it's not working on studio 8.04 x64

---

