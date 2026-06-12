---
title: "kernel 2.6.29.1,2.6.30rc3+fglrx 8.602 error!"
date: 2009-04-27
forum: Hardware
---

### Post by hanbin973 on 2009-04-27
I'm trying to configure kernel 2.6.29.1 or 2.6.30rc3 and catalyst 9.4 together. But when dkms runs and it starts to build the module, the error is keep coming. 
The error is 

fglrx (8.602) : Installing module.
.......(bad exit status: 7)
Build failed. Installation skipped.

I don't know why this error is coming. 

Anyone have any solution??

Please !!!

---

### Post by StuartN on 2009-04-27
> **hanbin973 said:**
> I'm trying to configure kernel 2.6.29.1 or 2.6.30rc3 and fglrx 8.602 together.

You are trying to compile the latest kernel with an old version of fglrx? I don't know why it will not compile, but it will not run even if it does because you need version 9.4 for compatibility with X server 1.6 (unless you regressed that too).

---

### Post by hanbin973 on 2009-04-28
No! ;;; 

Fgrlx 8.602 = 9.4 driver ...

9.4 supports X.org 1.6

9.3 = 8.593 , 9.4 = 8.602..

Fglrx 8.602 is the latest version..

---

### Post by Marat Galiev on 2009-04-28
How you try to install fglrx driver?
With installer or with apt-get?

---

### Post by hanbin973 on 2009-04-28
Fisrt, I installed my driver by generating the packages.
sh ati-driver-installer-9-4blahblah.run --buildpkg 
After the packages were generated, I installed the .debs. 

I didn't used apt-get.

Is the fglrx in the repository is 8.600 ( 9.4 beta ) ??;;;

I remember that it was 8.600 in the last day.

---

### Post by hanbin973 on 2009-05-02
Any solutions?? 

Any one using fglrx in 2.6.29 and higher versions???

---

### Post by hanbin973 on 2009-05-04
bump!

---

### Post by hanbin973 on 2009-05-05
any one have solution?

---

### Post by megawebmaster on 2009-05-07
I've got the same problem. I just compiled new kernel for my architecture (x86-64) and DKMS sends me info about fglrx.ko.
```
Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.29.1 (x86_64) first.
```

I just don't know how to solve this... I've tried building package, installing newest drivers from ATI/AMD - nope, nothing works...

EDIT: I just deleted this new kernel. I recompile 2.6.28 for x86-64 and thats just all... We will see ;)

---

### Post by martino2k8 on 2009-05-09
[http://www.linuxquestions.org/questions/linux-hardware-18/fglrx-9.3-patch-for-2.6.29.x-kernel-722858/](http://www.linuxquestions.org/questions/linux-hardware-18/fglrx-9.3-patch-for-2.6.29.x-kernel-722858/) <--- maybe this could help. Haven't tried myself yet.

---

### Post by hanbin973 on 2009-05-09
I tried that one..

The main thing is that, Ati will support 2.6.29 kernel from 9.6 driver.

So we need a patch to make fglrx work on 2.6.29. 

But... I don't have a folder called fglrx in /lib/modules ...

so i dosn't works... :(.

Arch linux uses a patch to make 9.4 work on 2.6.29 kernel.

One of my firend told me that it works on arch.

Any one have idea how to make these patches work?

The patch that arch users use is this. 

[http://aur.archlinux.org/packages/catalyst-ice/catalyst-ice/2.6.29.diff]("http://aur.archlinux.org/packages/catalyst-ice/catalyst-ice/2.6.29.diff")

It dosn't seems to have a certain phrase of something for arch.

---

