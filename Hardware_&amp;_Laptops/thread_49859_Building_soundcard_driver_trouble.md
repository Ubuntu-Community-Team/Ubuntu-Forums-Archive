---
title: "Building soundcard driver trouble"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by cacofonix on 2005-07-18
I'm following the guide on how to get the hda-intel sound card working from the ubuntu-wiki site (The first one). But I have hit a snag, configure ends with this:

```

checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... 2.6.10-5
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "yes"
configure: error: You have built-in ALSA in your kernel.

```

I have the linux-headers (both 2.6.10-5 and 2.6.10-5-686) I also have build-essential and ncurses-dev installed. Why is it complaining about no kernel compilers and about having alsa built in to the kernel?


**EDIT**
I uninstalled build-essential and the headers and re installed them now I get this error message:

```

checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```

why all of a sudden does it spit the dummy when I have done this plenty of times before with out a problem???

cacofonix

---

