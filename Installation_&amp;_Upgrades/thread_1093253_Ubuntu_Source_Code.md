---
title: "Ubuntu Source Code"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by grubby23 on 2009-03-11
Hi

I want to download the complete Ubuntu Source Code by doing the following:

grabher@grabher-desktop:/usr/src$ sudo apt-get install linux-source-2.6.27
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-source-2.6.27 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I thought that by doing this I will get all the required source files so that I can do some modifications in the kernel source. Anyone an idea why this is not happening? Is there maybe a direct link where I could download the complete course code? I would be interested in the linux-source-2.6.27-10 or linux-source-2.6.27-11 version!

Many thanks!

---

### Post by dgoosens on 2009-03-11
hi 

with sudo apt-get install you are telling your Ubuntu to install it

use wget instead, that will download the files

---

### Post by grubby23 on 2009-03-11
Thanks for your feedback. On the Ubuntu homepage I couldnt really find any
source code for the Linux Kernel to download (just the .iso file) so is it okay if I get the Kernel from here?

[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.11.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.11.tar.bz2)

Sorry for the stupid question ;)

---

### Post by Neo_The_User on 2009-03-11
You know thats just the kernel source right? Unless you are kernel developer, that's not going to mean anything to you. Due to the fact that you are asking where it is, I am assuming you are not a kernel developer. Btw, if you are a kernel developer, yes that is where the ubuntu patched kernel source is however the only advantage from compiling it is extra code in your kernel. I highly recommend building the upstream kernels from kernel.org if you don't need any of the weird fancy shmanzy extra junk in your kernel.

---

### Post by Dougie187 on 2009-03-11
If you want to get a package's source files using apt-get you can type

```
sudo apt-get source *packagename*
```

This should download the source. Granted, I don't know where it saves it so you might have to hunt for it. Keep in mind too, ubuntu doesn't really have any source. Its just a distribution of packages that have been put together and modified by developers. There are so many different packages that you would have to look at if you wanted to get the "source" but as it has been mentioned, that package that you are trying to get is just a linux kernel.

Edit: Here is the blurb from the man page for apt-get about the source option. The last paragraph is of particular interest

>        source
           source causes apt-get to fetch source packages. APT will examine
           the available packages to decide which source package to fetch. It
           will then find and download into the current directory the newest
           available version of that source package. Source packages are
           tracked separately from binary packages via deb-src type lines in
           the sources.list(5) file. This probably will mean that you will not
           get the same source as the package you have installed or as you
           could install. If the --compile options is specified then the
           package will be compiled to a binary .deb using dpkg-buildpackage,
           if --download-only is specified then the source package will not be
           unpacked.

           A specific source version can be retrieved by postfixing the source
           name with an equals and then the version to fetch, similar to the
           mechanism used for the package files. This enables exact matching
           of the source package name and version, implicitly enabling the
           APT::Get::Only-Source option.

           Note that source packages are not tracked like binary packages,
           they exist only in the current directory and are similar to
           downloading source tar balls.

---

### Post by Neo_The_User on 2009-03-11
^What he said

---

### Post by Seq on 2009-03-11
Running "apt-get source PACKAGE" will get you the source for PACKAGE. However, the kernel is packaged in a slightly different way than other packages. They are versioned so that multiple kernels can co-exist.

On my server, I am running kernel 2.6.27-13-server. To get the source code for this I would run the following command:

```
apt-get source linux-image-2.6.27-13-server
```

Or I can skip the lookup and typing and just run this. This will grab the source for the kernel I am currently running. Note that if you're not running the latest, you won't download the latest.

```
apt-get source linux-image-`uname -r`
```

EDIT: Looks like some of this was mentioned above. Just a few notes: sudo is not needed when you are getting source packages as you are not doing anything to your system. The package files will be placed in your current directory, so you may want to make a new one and switch to it first.

EDIT2: Actually, I would actually discourage using sudo here, even "just incase". It will cause your package source to be owned by root.

---

### Post by jocko on 2009-03-11
The package "linux-source-..." simply downloads the kernel source code (as a .tar.gz file) to your /usr/src/ directory.

---

### Post by grubby23 on 2009-03-11
Thanks for all your answers!

Basically, I wanna download a current Kernel and make some very basic changes to it. However, I fail
at the moment to get an original Kernel working. I have downloaded the current Kernel using the suggested
command:

apt-get source linux-image-`uname -r`

After that I copy the config file from a working kernel doing the following:

sudo cp /boot/config-2.6.27-11-generic ./.config

Now I call "make menuconfig" and select than as a configuration file the file from the working Kernel

I compile the Kernel with make -j4 bzImage and I get during the build a WARNING: modpost: Found 15 section mismatch(es).

sudo cp arch/i386/boot/bzImage /boot/mynewkernel 

copies the kernel into the boot directory and then I made the following changes to GRUB so that I can use the modified Kernel:

# New Kernel
title		Ubuntu 8.10, Modified Kernel
uuid		ad1a7653-0c25-4657-9ec6-056d53ca146b
kernel		/boot/mynewkernel root=UUID=ad1a7653-0c25-4657-9ec6-056d53ca146b ro quiet splash 
quiet

# Original Kernel
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		ad1a7653-0c25-4657-9ec6-056d53ca146b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ad1a7653-0c25-4657-9ec6-056d53ca146b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

However, if I select on boot the new Kernel I get the following message: Kernel Panic - not syncing: VFS: Unable to mount root fs
on unknown-block(0,0);

Anyone an idea what could have gone wrong? It is quite depressing that I even cant get an ORIGINAL kernel with an ORIGINAL config file running....

Many thanks!

---

### Post by Seq on 2009-03-11
> **grubby23 said:**
> Thanks for all your answers!

Basically, I wanna download a current Kernel and make some very basic changes to it. However, I fail
at the moment to get an original Kernel working. I have downloaded the current Kernel using the suggested
command:

apt-get source linux-image-`uname -r`

After that I copy the config file from a working kernel doing the following:

sudo cp /boot/config-2.6.27-11-generic ./.config

Now I call "make menuconfig" and select than as a configuration file the file from the working Kernel

I compile the Kernel with make -j4 bzImage and I get during the build a WARNING: modpost: Found 15 section mismatch(es).

sudo cp arch/i386/boot/bzImage /boot/mynewkernel 

copies the kernel into the boot directory and then I made the following changes to GRUB so that I can use the modified Kernel:

# New Kernel
title		Ubuntu 8.10, Modified Kernel
uuid		ad1a7653-0c25-4657-9ec6-056d53ca146b
kernel		/boot/mynewkernel root=UUID=ad1a7653-0c25-4657-9ec6-056d53ca146b ro quiet splash 
quiet

# Original Kernel
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		ad1a7653-0c25-4657-9ec6-056d53ca146b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ad1a7653-0c25-4657-9ec6-056d53ca146b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

However, if I select on boot the new Kernel I get the following message: Kernel Panic - not syncing: VFS: Unable to mount root fs
on unknown-block(0,0);

Anyone an idea what could have gone wrong? It is quite depressing that I even cant get an ORIGINAL kernel with an ORIGINAL config file running....

Many thanks!

Probably because it expects an initrd, among other things. The linux-image package I linked to is the debianized source package for the kernel. You would typically build this as a package with e.g. 'debuild'. This would give you several packages for the image, modules, etc, and would allow your kernel to be tracked via apt. Changes to configuration is handled in the debian/ directory.

If you just want to roll your own one-off kernel and avoid the whole package situation, then the linux-source pages mentioned by others above are probably more what you are after.

---

### Post by Neo_The_User on 2009-03-11
Ugh you're building the whole kernel all backwards.

*shakes his head*

First off, whoever said "build it in /usr/src" is wrong.

Second, don't build it with make -j4 whatever.

Third, don't build it using make if you don't know what you're doing.

I'd offer the correct advice but for linux beginners, I'm not going to bother. My advice: Don't build kernels.

---

### Post by grubby23 on 2009-03-11
Thanks for the comments once again. I tried to follow the Kernel introduction written by some IBM people where you would guess that they know what they are talking about

[http://www.ecse.rpi.edu/Homepages/shivkuma/teaching/fall2006/class07/l-kernelhack2-a4.pdf](http://www.ecse.rpi.edu/Homepages/shivkuma/teaching/fall2006/class07/l-kernelhack2-a4.pdf)

However, if there are any better tutorials out there I would be keen to know about them!

---

### Post by oldos2er on 2009-03-11
You might want to look into a program called kernelcheck.

---

### Post by jocko on 2009-03-12
> **grubby23 said:**
> However, if there are any better tutorials out there I would be keen to know about them!
[Here]("http://ubuntuforums.org/showthread.php?t=311158") is one good tutorial.

---

