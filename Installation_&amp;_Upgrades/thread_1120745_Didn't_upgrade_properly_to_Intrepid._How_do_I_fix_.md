---
title: "Didn't upgrade properly to Intrepid. How do I fix it?"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by VotaVader on 2009-04-09
Hello!
I migrated from Hardy to Intrepid a while back, and while I was doing the upgrade, the wizard prompted me many times if I wanted to change my menu.something (the one that usually is presented on the GRUB screen for multi-boot). Anyway, I always told it to keep the one I'd customized (the old one) and not replace it with a new one. In retrospect, this might have been a mistake, because apparently now my OS doesn't quite know what version it is...
For example, the command cat /etc/issue gives back Ubuntu 8.10 \n \l, and that seems to be the case for most purposes, but for some things, it doesn't quite work. Of course my GRUB screen still has the option of going into the Ubuntu 8.04 2.6.24-21-generic instead of 8.10 (although it boots up Intrepid), but the thing that most bothers me is that when building certain things, it gets cranky.
Today I tried upgrading my nVidia driver from the 177 to the 180 for my GeForce 8600GS (laptop), and when I rebooted, I got a bunch of errors, and the only way to start X was on low graphics mode (which I am using right now at 800x600 res... ¬¬). I fidgeted around for a while, and tried to reinstall the driver through Synaptic. It seemed to install fine, but looking at the Terminal, I realized there were some build errors:

```
Error! Your kernel source for kernel 2.6.24-21-generic cannot be found at /lib/modules/2.6.24-21-generic/build or /lib/modules/2.6.24-21-generic/source.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.24-21-generic (i686) first.
Done.
```

So I did. I ran the following commands, and these were their outputs.
```
pedro@pedro-laptop:~$ sudo dkms add -m nvidia -v 180.11 -k $(uname -r)

Error! DKMS tree already contains: nvidia-180.11
You cannot add the same module/version combo more than once.
pedro@pedro-laptop:~$ sudo dkms build -m nvidia -v 180.11 -k $(uname -r)

Error! Your kernel source for kernel 2.6.24-21-generic cannot be found at
/lib/modules/2.6.24-21-generic/build or /lib/modules/2.6.24-21-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
```

By now I'd figured out that the driver was trying to build from the source code of the previous version (Hardy), and of course, wasn't finding it. So I gave DKMS the directory of the 2.6.27-11-generic code (for Intrepid) to see what happened. It almost worked...
```
pedro@pedro-laptop:~$ sudo dkms build -m nvidia -v 180.11 -k $(uname -r) --kernelsourcedir /lib/modules/2.6.27-11-generic/build

Preparing kernel 2.6.24-21-generic for module build:
(This is not compiling a kernel, just preparing kernel symbols)
Storing current .config to be restored when complete
Running Generic preparation routine
make mrproper.......
using /lib/modules/2.6.27-11-generic/build/.config
(I hope this is the correct config for this kernel)
make oldconfig......
make prepare-all.....(bad exit status: 2)

Building module:
cleaning build area....
make KERNELRELEASE=2.6.24-21-generic module KERNDIR=/lib/modules/2.6.24-21-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/2.6.27-11-generic/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.24-21-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/180.11/build/ for more information.
0
0
```

I looked at the log, and the error shown there was:
```
*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1
```

So, as you can see, I'm sort of stuck in between Hardy and Intrepid, and programs tend to get confused as to which one I'm using. I don't know, being fairly new to Linux, how to correct this type of problem, and would very much appreciate any help I could get on this topic. The idea is to make the whole OS know I'm with Intrepid now XD.
Thanks!

---

### Post by VotaVader on 2009-04-09
Bump!
Please some help on this! I can't stand this 800x600 screen, and I can't watch videos or play games!
I've seen that many people are having problems with the new nVidia driver. Maybe this could help them too...

---

### Post by pbotros1234 on 2009-04-09
I think the problem is that you're booting into an old kernel (the 2.6.24 kernel instead of 2.6.27). Post your /boot/grub/menu.lst, and the result of:
```
ls -l /boot
```

---

