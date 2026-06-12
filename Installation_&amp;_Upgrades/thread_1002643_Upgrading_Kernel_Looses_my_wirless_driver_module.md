---
title: "Upgrading Kernel Looses my wirless driver module"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by SynDaily on 2008-12-05
Hello,

I'm a bit grumpy about upgrading. Every time I do a kernel upgrade my wireless drivers do not get included.

I use a Medion akoya laptop, with a ralink wireless ethernet card built in.

After the kernel upgrades I need to:

# make
# cp ./os/linux/rt2860sta.ko /lib/modules/2.6.24-22-generic/kernel/net/wireless/ 
# depmod -a
# init 6

My question is: can I put the source code for the module anywhere that it will be picked up during upgrading?

or:

Is there an upgrade script that I can append these instructions to?

Cheers

Simon

---

### Post by regala on 2008-12-05
> **SynDaily said:**
> Hello,

I'm a bit grumpy about upgrading. Every time I do a kernel upgrade my wireless drivers do not get included.

[...]

My question is: can I put the source code for the module anywhere that it will be picked up during upgrading?

or:

Is there an upgrade script that I can append these instructions to?



nope. not yet. As long as there is no debian/ubuntu source package for your out-of-tree driver, there is not. I do not know about efforts integrating it in Jaunty, maybe it is being taken care of at the moment. When there is a rt2860-source package, DKMS will take care of rebuilding all your external kernel modules.

cheers

---

### Post by SynDaily on 2008-12-05
> **regala said:**
> nope. not yet. As long as there is no debian/ubuntu source package for your out-of-tree driver, there is not. I do not know about efforts integrating it in Jaunty, maybe it is being taken care of at the moment. When there is a rt2860-source package, DKMS will take care of rebuilding all your external kernel modules.

cheers

So if I where to build the source code into a rpm, would that stick around between updates?

---

### Post by regala on 2008-12-09
> **SynDaily said:**
> So if I where to build the source code into a rpm, would that stick around between updates?

the file would stick around. But you must understand that your problem is not because of kernel upgrades removing your driver files, but, kernel upgrades obsoleting these files: drivers must be compiled against the version they will run with, and kernel upgrades bump their revisions => your driver doesn't work anymore. that's why rebuilding the driver actually works. But putting stuff into an rpm file will not take care of rebuilding against your latest kernel sources...

On the other hand, DKMS is a framework/tool that automagically recompile your external drivers against the latest kernel after a kernel upgrade. This is what you're looking for. But to have this working, the driver must be source-packaged by Ubuntu, to have DKMS to be taken care of. A little patience/a little bugging on Launchpad should wake up developer. But it won't be before Jaunty I'm afraid

---

