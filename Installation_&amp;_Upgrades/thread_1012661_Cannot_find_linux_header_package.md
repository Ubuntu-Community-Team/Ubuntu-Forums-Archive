---
title: "Cannot find linux header package"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by sygard on 2008-12-16
Hi!

I just recently rented me this virtual server, and it's running ubuntu with a wierd kernel in it.

uname -r says:
```

2.6.18-028stab059.5-ent

```

And when I try to install the linux headers, apt-get cannot find the package:
```

$ apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.18-028stab059.5-ent

```

so, what kernel header package should I install???

Thanks!

---

### Post by joff13 on 2008-12-16
Hi sygard,

I don't think ```
2.6.18-028stab059.5-ent
``` is an officially released kernel. Most likely someone re-compiled the kernel. That's why you don't find it in the repos....

---

### Post by sygard on 2008-12-16
yeah, kinda figgured that...

Anyway, I'm also missing the tun module, is there anyway to install that?

---

### Post by sygard on 2008-12-16
thought I'd install a standard kernel, but it seems I am a little low on memory for this, don't quite see why, it's supposed to be 300mb, which should be enough...
```

root@sygard:~# apt-get install linux-image-2.6.24-22-virtual
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.24-22-virtual is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.24-22-virtual (2.6.24-22.45) ...
Running depmod.
WARNING: Can't read module /lib/modules/2.6.24-22-virtual/kernel/drivers/input/evdev.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-22-virtual/kernel/drivers/input/evbug.ko: Cannot allocate memory
FATAL: Could not open /lib/modules/2.6.24-22-virtual/modules.dep.temp for writing: Cannot allocate memory
Failed to run depmod
dpkg: error processing linux-image-2.6.24-22-virtual (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.24-22-virtual
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help will be appriciated !

---

### Post by albinootje on 2008-12-16
> **sygard said:**
> 
WARNING: Can't read module /lib/modules/2.6.24-22-virtual/kernel/drivers/input/evdev.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-22-virtual/kernel/drivers/input/evbug.ko: Cannot allocate memory
FATAL: Could not open /lib/modules/2.6.24-22-virtual/modules.dep.temp for writing: Cannot allocate memory


You're renting a VPS somewhere, right ?
The VPS software i use at work doesn't even have a kernel in the VPS-es itself.

And if you want to use the tun device, why not ask the hosting company ?
You can also ask them about compiling software, and which kernel-headers are needed.

---

### Post by sygard on 2008-12-16
yeah, it's a VPS system... damn, I'm a little disappointed, I thought I'd get a full system to play with, but it seems you're right. I switched to the debian package, and it's running the exact same kernel.

I'll contact the admins there, maybe they'll allow me to use the tun module.

Thanks though!

---

### Post by albinootje on 2008-12-16
> **sygard said:**
> yeah, it's a VPS system... damn, I'm a little disappointed, I thought I'd get a full system to play with, but it seems you're right. I switched to the debian package, and it's running the exact same kernel.

Depending on the VPS software (on the host), and on how it was set up for you, you will basically get a full system to play with.
But some things are a little different.

If you really need to compile software for it, you could compile it on another system, use the "checkinstall" software to create a deb file, and install it in the VPS.

---

### Post by RJARRRPCGP on 2008-12-17
You forgot to run apt-get as root, with sudo!

---

### Post by Drunken on 2009-07-16
It sounds like you are running an OpenVZ virtual machine.
These have custom kernels that are shared between all guests (customers like you) and they cannot be modified as far as I know. You will also have other limitations such as mounting, etc due to the fact all guest machines share the same OS. This is known as a virtual container and you are just one of the containers.

If you want a proper sandbox to play with, you might look into renting a VPS that uses real virtualization/paravirtualization such as Xen, QEMU or VMWare (Xen hosts are very common).

Your hosting company should tell you what virtualization software they use before you signup.
Also stay away from hosts running Virtuozzo.

---

### Post by albinootje on 2009-07-17
> **Drunken said:**
> 
Also stay away from hosts running Virtuozzo.

Why so ?

---

### Post by Drunken on 2009-07-18
> **albinootje said:**
> Why so ?

Because I'm pretty sure it works the same way as OpenVZ and won't let him modify the kernel.

---

