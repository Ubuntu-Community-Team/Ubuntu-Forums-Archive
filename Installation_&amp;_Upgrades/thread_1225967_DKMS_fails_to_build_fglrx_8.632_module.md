---
title: "DKMS fails to build fglrx 8.632 module"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by chuck_notorious on 2009-07-29
Hi guys,

I'm trying to install the proprietary ATI drivers on my Ubuntu Studio system. I'm running a custom realtime kernel to get around linux-rt package, but that means I can't install the driver using the restricted driver manager.

Having built the deb packages from the ATI binary distribution I'm not able to install fglrx-kernel-source_8.632-0ubuntu1_i386.deb. DPKG has the following error:
```
charles@balthazar:~/Downloads/ATI$ sudo dpkg -i fglrx-kernel-source_8.632-0ubuntu1_i386.deb 
(Reading database ... 237827 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 2:8.632-0ubuntu1 (using fglrx-kernel-source_8.632-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (2:8.632-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build

Error!  Build of fglrx.ko failed for: 2.6.29.6-rt23-cpm-rt-090728 (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.632/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.29.6-rt23-cpm-rt-090728 (i686) first.
Done.

charles@balthazar:~/Downloads/ATI$ 
```

I realise that this is problem occurs for those running a custom kernel so I ran the command for dkms to build the kernel module which also ended with an error:
```
charles@balthazar:~$ sudo dkms build -m fglrx -v 8.632 -k `uname -r` 
[sudo] password for charles: 

Kernel preparation unnecessary for this kernel.  Skipping...
applying patch fglrx-rt-compat.patch...patching file firegl_public.c
Hunk #1 succeeded at 1285 (offset -67 lines).
Hunk #2 succeeded at 1310 (offset -67 lines).


Building module:
cleaning build area....
pushd /var/lib/dkms/fglrx/8.632/build; sh make.sh --nohints --uname_r=2.6.29.6-rt23-cpm-rt-090728; popd....

Error!  Build of fglrx.ko failed for: 2.6.29.6-rt23-cpm-rt-090728 (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.632/build/ for more information.
charles@balthazar:~$
```

The make.log file is unfortunately empty, so I have no clue about what I could do to solve this problem.

Is there anybody that could suggest a good strategy to build this driver?

Thanks for your help,

--Charles.

---

### Post by chuck_notorious on 2009-07-29
I think the answer is that fglrx is incompatible with new versions of the kernel. Unlucky for me. Maybe soon everything will be fixed.

Some people have been able to patch the fglrx source, but I haven't found a way to do this that works for me yet.

--C

---

### Post by Stochastic on 2009-09-02
I think quite often ATI releases a new fglrx version very close to the Ubuntu release date, in order to be compatible with the latest common kernel.

That's why I use the open source Radeon driver rather than the fglrx driver (as of Jaunty it's good enough for everything I need).

---

### Post by chuck_notorious on 2009-09-07
There's now a new version of fglrx now that works fine.

---

### Post by kaspien on 2010-01-23
> **Stochastic said:**
> I think quite often ATI releases a new fglrx version very close to the Ubuntu release date, in order to be compatible with the latest common kernel.

That's why I use the open source Radeon driver rather than the fglrx driver (as of Jaunty it's good enough for everything I need).

Which drivers do you use?


I get the same error as the op:
> Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.

I'm running Ubuntu 9.10 x64 trying to install: fglrx-kernel-source_8.593-0ubuntu1_amd64.deb

---

### Post by zx1986 on 2010-03-14
I got the same problem !!

I'm running Ubuntu 9.10 x64 too,
I had tried :

ati-driver-installer-10-2-x86.x86_64.run (from ATi.com)
ati-driver-installer-9-9-x86.x86_64.run (from ATi.com)

do not work at all !!

my graphic card is (ATi Integrated/Motherboard) Radeon HD 3200.

help please :-(

---

### Post by chuck_notorious on 2010-03-14
Hi everybody,

Sorry, I can't contribute any more to this thread. This was a problem I had in 9.04 in July 2009, not 9.10. Everything worked better for me with the newer version.

--Charles

---

