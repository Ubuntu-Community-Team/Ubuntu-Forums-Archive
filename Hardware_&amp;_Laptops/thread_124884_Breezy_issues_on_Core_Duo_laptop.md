---
title: "Breezy issues on Core Duo laptop"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by drosky on 2006-02-02
I have installed Breezy on a new Dell Inspiron 9400 with a 2GHz Core Duo processor.  There are a few issues that appear to be specific to Ubuntu, in the sense that they are not issues with SUSE 10.0, which I also installed:

1. The i686-SMP Kernel does not work properly.  It boots, but the system freezes after a few moments.

2. Suspend-to-disk and RAM both do not work (non-SMP kernel).  They work fine on slightly older centrino laptops.

Has anyone else tried SMP  or suspend on a Core Duo?

Regards,
Dave

---

### Post by Toontwnca on 2006-02-02
[QUOTE=drosky]I have installed Breezy on a new Dell Inspiron 9400 with a 2GHz Core Duo processor.  There are a few issues that appear to be specific to Ubuntu, in the sense that they are not issues with SUSE 10.0, which I also installed:

1. The i686-SMP Kernel does not work properly.  It boots, but the system freezes after a few moments.

2. Suspend-to-disk and RAM both do not work (non-SMP kernel).  They work fine on slightly older centrino laptops.

Has anyone else tried SMP  or suspend on a Core Duo?

Regards,
Dave[/QUOTE]


A couple of possibilities come to mind.

1. The CoreDuo is a fairly new chip. (I think). Breezy may not be ready for
    it. (probably wrong about this)
2. The CoreDuo is a dual processor on a single die which in turn uses
    a single socket. The -smp kernels are used for dual-socket mobo's; I
    believe. (probably wrong about this too.) So it would not be needed.
    Just the regular kernel may work.

Someone feel free to correct me, as I have no idea as to the accuracy of 
what I'm saying.

---

### Post by drosky on 2006-02-03
I think you're probably right on point 1 - it is new, and the 
current breezy kernel is probably untested on it.

I think point 2 might not be correct.  AFAIK, the SMP kernels
should work for any case where the system is seen by the OS
as having two processors, even if they are on the same die.
For example, the Breezy SMP kernel works fine on my P4 with
hyperthreading, which is also a single die that appears as two
processors to the OS.  Also, Kernels from SUSE (2.6.13) and
Arch (2.6.15) work fine in SMP mode.

I should point out that the current Dapper kernel seems to work
on the core duo in SMP, but I thought there may be some interest in 
getting the currently released version working.

This is a fairly bleeding-edge laptop, and so far out of 4
distros, only SUSE 10.0 had everything working right out of
the box (except the wireless and the expressCard, which don't have 
any Linux drivers yet).  I don't mind using SUSE, but I like Ubuntu 
better, so I've been trying to make it work ;)  I may just switch to
Dapper if it seems stable enough.

[QUOTE=Toontwnca]A couple of possibilities come to mind.

1. The CoreDuo is a fairly new chip. (I think). Breezy may not be ready for
    it. (probably wrong about this)
2. The CoreDuo is a dual processor on a single die which in turn uses
    a single socket. The -smp kernels are used for dual-socket mobo's; I
    believe. (probably wrong about this too.) So it would not be needed.
    Just the regular kernel may work.

Someone feel free to correct me, as I have no idea as to the accuracy of 
what I'm saying.[/QUOTE]

---

### Post by avilella on 2006-02-05
If your CPU has more than one processing unit (physical or virtual) you
should use the SMP kernel.

---

### Post by spiritofreason on 2006-02-16
The 686-smp kernel hangs when attempting to start PCMCIA services.  If you just use BUM or sysv-rc-conf to disable it, everything works fine.

---

