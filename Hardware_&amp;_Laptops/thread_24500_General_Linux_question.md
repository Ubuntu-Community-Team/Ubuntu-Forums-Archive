---
title: "General Linux question"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by Bashar on 2005-04-07
Hi,
What does it mean to "have the kernel source installed, or that you modify the makefile so that the INCLUDES_PATH points to your includes (usually /usr/include)"??
Thank you for your time

---

### Post by lao_V on 2005-04-07
[QUOTE=Bashar]Hi,
What does it mean to "have the kernel source installed[/QUOTE]

it means install the header files for your linux kernel. You can install this in synaptic if you type 'linux-headers' in the search box and select the one for your linux (if you want to know which kernel you're using type uname -r in the terminal)

[QUOTE=Bashar] or that you modify the makefile so that the INCLUDES_PATH points to your includes (usually /usr/include)"??
Thank you for your time[/QUOTE]

I'm assuming you are trying to compile your own program. If that's the case then look in the program directory and there should be a makefile. Just open it and find the INCLUDES_PATH and set it to /usr/src/linux-headers-(your kernel)/include

---

### Post by az on 2005-04-07
"What does it mean to "have the kernel source installed, or that you modify the makefile so that the INCLUDES_PATH points to your includes (usually /usr/include)"??"


Unix systems need a kernel to run.  Actually, everyting runs on top of that kernel.  The linux kernel is monolythic, meaning that everything is at the same place.  Other kinds of Unix kernels are microkernels which are very small and interface with a bunch of other processes to get 'kernel' things done - like running devices  and taking care of memory.

Traditionaly, it is easier to get things done using a monolythic kernel, but it is harder to change things since when you break something, you break the whole kernel.  In a mircokernel, you can work on one part at a time.  Object orientation.

Anyway, the linux kernel has struck a balance in that although it is monolythic, you can still add modules to it.  The thing is, that each module has to be compiled for the specific kernel.

A module written for kernel 2.4.18-bf2.4 will not work for 2.4.21.  It will definitely not work for 2.6.10.5!

But, the advantage of open source is that you have the source.  You take the source and compile it and you can run it.  

If you are running some obscure form of Unix which has no precompiled packages, you can still download all if the gnome source and compile it and run gnome 2.10, if you want.  This is just an example, since this has nothing to do with the kernel.

Since you are already running a linux kernel, to add to that kernel, you need to have the source code (which has many many configuration options.  Not all of the options are running. )  A configured source code for the kernel would take up something like 200 megs of hard drive space.

You do not need that for most things.  In fact, it is only a very small percentage of users who will have to compile any kernel modules at all.  That is why the kernel-source is not installed by default.  For your convenience, the header files have been packaged.  You can install them, if you need.

The kernel headers (linux-headers) allow you to compile kernel modules for your kernel without taking up all that hard drive space.  They are the minimum parts of the configured kernel source code for your running kernel.

There.


Install build-essential and linux-herders(-yourkernelversion)

---

