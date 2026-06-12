---
title: "Where to find Kernel Sources"
date: 2005-01-15
forum: Installation &amp; Upgrades
---

### Post by Benko on 2005-01-15
Hi,

I installed ubuntu this morning.

But trying to install my wlan driver, the driver cannot find the right kernel sources :
The installer tell me :

Linux source directory [/lib/modules/2.6.8.1-4-386/build]:
Linux source tree /lib/modules/2.6.8.1-4-386/build is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed


Where can I find the sources ? ???
I tried with Synaptic but even with sources 2.6.8.1 installed, it doesn' work

Thanks for your help

---

### Post by Randabis on 2005-01-15
[QUOTE=Benko]Hi,

I installed ubuntu this morning.

But trying to install my wlan driver, the driver cannot find the right kernel sources :
The installer tell me :

Linux source directory [/lib/modules/2.6.8.1-4-386/build]:
Linux source tree /lib/modules/2.6.8.1-4-386/build is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed


Where can I find the sources ? ???
I tried with Synaptic but even with sources 2.6.8.1 installed, it doesn' work

Thanks for your help[/QUOTE]
 When you installed the sources, did you go into /usr/src and extract the tarball? When you install linux-sources it only puts them in the form of a tarball into that directory. I'm not sure why it does it this way, but all you have to do is extract it. You also might want to install kernel-headers as well.

---

### Post by stoneguy on 2005-01-15
[QUOTE=Benko]Hi,

I installed ubuntu this morning.

But trying to install my wlan driver, the driver cannot find the right kernel sources :
The installer tell me :

Linux source directory [/lib/modules/2.6.8.1-4-386/build]:
Linux source tree /lib/modules/2.6.8.1-4-386/build is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed


Where can I find the sources ? ???
[/QUOTE]

Did you install build-essential? And apt-get your source? See [http://www.ubuntuforums.org/showthread.php?t=10364](http://www.ubuntuforums.org/showthread.php?t=10364)
for relevant discussion.

---

### Post by Benko on 2005-01-16
Thanks.

I installed the build-essential
I untaredt the package of the sources but I still have this message :

[I]Linux source directory [/lib/modules/2.6.8.1-4-386/build]:
Linux source tree /lib/modules/2.6.8.1-4-386/build is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed
[/I]

I checked the folder :
I have a directory /lib/modules/2.6.8.1-4-386/ but not the "build" directory

Thanks for you help

---

### Post by az on 2005-01-16
" untaredt the package of the sources but I still have this message :

Linux source directory [/lib/modules/2.6.8.1-4-386/build]:"

What does that last lkine say?  It is looking for the sources in the /lib/modules/2.6.8.1-4-386/build directory.  Where did you put your sources?  In /usr/src/kernel-source/2.6 or something.

To build a driver modules, you not only need the sources, but you need them to be configured to match your running kernel.  You would need to copy your current kernel's config file found in /boot to the kernel source tree.  You would then need to compile the kernel (or at least start the compilation - just make the headers) so that you can compile extra stuff (like your module) with them.

Just make your life easier and install the linux-headers package.  It installes the header files for your kernel.  It is all youo need to compile extra drivers for your kernel.  When asked where is your kernel tree, just say /usr/src/linux-headers-2.6-8.1-4-386


You may also just make a symlink (which is probably what the documentation for your driver has told you to do) from the tree to /lib/modules/2.6.8.1-4-386/build

---

### Post by Benko on 2005-01-16
[QUOTE=azz]" untaredt the package of the sources but I still have this message :

Linux source directory [/lib/modules/2.6.8.1-4-386/build]:"

What does that last lkine say?  It is looking for the sources in the /lib/modules/2.6.8.1-4-386/build directory.  Where did you put your sources?  In /usr/src/kernel-source/2.6 or something.

To build a driver modules, you not only need the sources, but you need them to be configured to match your running kernel.  You would need to copy your current kernel's config file found in /boot to the kernel source tree.  You would then need to compile the kernel (or at least start the compilation - just make the headers) so that you can compile extra stuff (like your module) with them.

Just make your life easier and install the linux-headers package.  It installes the header files for your kernel.  It is all youo need to compile extra drivers for your kernel.  When asked where is your kernel tree, just say /usr/src/linux-headers-2.6-8.1-4-386


You may also just make a symlink (which is probably what the documentation for your driver has told you to do) from the tree to /lib/modules/2.6.8.1-4-386/build[/QUOTE]
 Ok, I tried to Install the linux header package. It seems that it is the easier method.
But there is a lot of "header" named packages in synaptic, which on is it ?

---

### Post by az on 2005-01-17
What kernel do you have installed(linux-image package)?  Look in synaptic.  Use the matching linux-headers.

---

