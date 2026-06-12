---
title: "Questions about Linux drivers"
date: 2008-07-13
forum: Hardware
---

### Post by teqnilogik on 2008-07-13
I'm relatively new to Linux.  I'm an advanced Windows and PC user and I can work my way around the Linux command line and Linux itself but I'm a little confused on how drivers in Linux work.

I've read that drivers come pre-compiled into the Linux kernel.  I've also read that you can compile drivers into the kernel itself or load them as kernel modules.  

I have installed drivers before and when my kernel was updated by Ubuntu the drivers were no longer installed.  So I assume that means that the install routine the driver had me use (make install) compiled the driver direct into the kernel.  Do most drivers get compiled into the kernel itself or load as modules?  Also, do you need to recompile modules when you update your kernel?  It seems rather inconvenient to need to reinstall all the drivers you installed everytime a kernel update is released.

I'm just trying to understand how Linux driver installation works.  I like Linux and would like to learn more.  I did do a search for this information but I was unable to find any good resources on this topic.  Any answers would be greatly appreciated.  Thank you in advance.

---

### Post by matt$2 on 2008-07-13
Good question..   very good.   here we go.

Do you have the headers installed.  If not, it can be done.

go look in /lib/modules/ -- kernel-version--  /
and then ofcourse in the subdirectory drivers.

and have a long peruse.  They're all there.

Drivers is an interesting challenge in linux. Generally any user
relies upon the distribution to have kernels covered.  You can acquire packages which are drivers not present in the system.  
Then they demand the kernel headers be in place.  The only distro that standard supplies, in fact demands, having the header in place and compiling is gentoo.. They are excellent.
I've been there done that.  I learned heaps from their standard documentation. ... as good as Ubuntu is.  the moderators will freak when they read this.

When you install a package that adds drivers, they require the kernel headers.  The installation then incorporates the package into the kernel proper, and adds the essential core directories and drivers to /lib/modules/that-kernel-version.

That should be enough for starters.

Look through gentoo's documentation if you want to go further.

---

### Post by eldragon on 2008-07-13
may i add, that if you install external drivers (modules) from another source. they are meant for that kernel in particular (if they were already compiled).

those modules will not work when there is a new kernel update.
so your choices are:
a) get a new binary module and place it where it should.

b) just get the source, the kernel headers, and recompile the module each time there is a kernel update.

option b may seem as the more difficult, but its usually easier to just make, and make install the same source, which usually works with the new kernel. 

one example is the virtual box kernel module. after every update, you need to do
```

sudo /etc/init.d/vboxdrv setup

```

which is a script that will compile and install  the new kernel module.


in my own world i have to build and install 3 modules after every kernel update.

rt73 from serialmonkey (wireless)
vboxdrv
cpufreq from phc for undervolting.


i hope i cleared some more :)

---

### Post by teqnilogik on 2008-07-13
So are modules compiled into the kernel?  Are all drivers modules?  Guess I'm not understanding what gets compiled into the kernel and what are loaded as modules.

---

### Post by issih on 2008-07-13
Nope, the drivers are not technically compiled into the kernel...They are compiled to be compatible WITH a specific kernel. When the module is compiled, it needs the header files (part of the source code) of the kernel being used in order to be compiled correctly. Consequently a module is tied to the kernel version it was compiled for. They are separate entities, and are loaded at run time by the kernel, but they must match versions.

If you compiled your own module, then there is a good chance you will need to recompile your modules when the kernel is updated. To do this you must ensure you have the latest kernel headers installed and then rerun the compilation scripts.

It is possible that the module will still work if nothing changed in the section of the kernel you are using between the versions you are talking about, but there are no guarantees.

Hope that helps :)

P.S. you almost certainly can have drivers actually compiled into your kernel if you roll your own kernel, but its not that common to do that anymore

---

