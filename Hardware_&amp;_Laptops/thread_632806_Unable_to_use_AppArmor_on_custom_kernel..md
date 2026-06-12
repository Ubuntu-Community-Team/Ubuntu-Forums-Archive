---
title: "Unable to use AppArmor on custom kernel."
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by hardran3 on 2007-12-05
After I [compiled a kernel with SLAB so suspend would work with the ATI fglrx drivers]("http://blog.vaxius.net/?p=19"), apparmor no longer loads. I tried to [recompile it the Fiesty way]("https://help.ubuntu.com/community/AppArmor"), but the apparmor-modules-source package is not available. Any help would be appreciated, thanks.

---

### Post by Friek on 2007-12-06
Well, if the modules aren't available and you didn't apply the patches needed for apparmor (I guess it's not included in vanilla kernels), it's not going to work ;)
The patches are probably somewhere on the [apparmor site](http://www.novell.com/linux/security/apparmor/).

---

### Post by hardran3 on 2007-12-06
I used the Linux source package from the repositories, not a vanilla package. it should have the patches applied, no? I used the config from the generic Gutsy kernel, and all I did was change SLUB --> SLAB and changed the processor type to pentiumM.

---

### Post by Friek on 2007-12-06
My apologies. I thought you used a vanilla kernel.
Anyway, the apparmor module source appears to be available [here](http://packages.ubuntu.com/feisty/base/apparmor-modules-source). Strange thing is that I can't find them via apt-cache even though I have the universe repositories enabled..

---

### Post by hardran3 on 2007-12-06
Yes, and this is the problem. According to [this ]("https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/156071")

> On Tue, Oct 23, 2007 at 03:25:01AM -0000, g2g591 wrote:
> Gutsy has no package containing the source for the apparmor module/s, so
> those of us who like to compile and use the latest kernel (no offense to
> the kernel devs who took all that time customizing it) can't use
> apparmor.
>

You can find the source of the kernel module in
linux-ubuntu-modules-2.6.22 source package, under
ubuntu/security/apparmor.

feisty used to provide an apparmor-kernel-source package that could be
used with m-a. It was dropped during gutsy because the kernel module was
included in linux-ubuntu-modules.

So do I just need to install linux-ubuntu-modules? I am a noob, be gentle :)

---

### Post by sodster on 2007-12-28
have you managed to get it working?

---

### Post by ieee802 on 2008-03-17
has anyone found a way to get it working?
i've downloaded linux-ubuntu-modules-2.6.22 source from launchpad but i cannot get it to compile in any way.
can someone help me to get it to compile? thanks

---

### Post by djuhl30 on 2008-03-20
First of all, I'd like to say I am not a expert.  So take this post at your own risk.  The only reason I try to compile the latest kernel is cause I can, and the Ubuntu developers would probably shoot me for doing so.  The best advice is if the Ubuntu kernel works don't worry about it.  But you needed to.  I found these kernel patches for apparmor the link is here.
[http://forge.novell.com/modules/xfcontent/file.php/apparmor/kernel-patches-2.6.24.tgz](http://forge.novell.com/modules/xfcontent/file.php/apparmor/kernel-patches-2.6.24.tgz)
 
Playing with it I discovered this:
There is a file called series in the extracted directory that tells you the order you need to apply the patches.  It is for the 2.6.24 kernel.  I patched it first and patched it up to 2.6.24.3 getting the patch from [www.kernel.org](www.kernel.org).  It patched fine and compiled fine.  Whether it works fine I don't know my computer hasn't blown up yet.  For some reason I wasn't given the option to compile apparmor as a module, and I disabled SElinux all together.  This is on my acer laptop.  I need to read the documentation , on apparmor and play with it even I really don't have a reason to do so.  Best way to learn something is to mess  it  to up no?

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
David

---

