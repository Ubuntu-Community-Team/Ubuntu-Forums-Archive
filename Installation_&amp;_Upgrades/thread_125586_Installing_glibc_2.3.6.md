---
title: "Installing glibc 2.3.6"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by Mishal on 2006-02-04
I use Hoary Hedgehog and for various reasons not upgrading to Breezy. However, many of my software requires the latest glibc and gtk.

Since they are not available from Synaptic, I downloaded the tar files and intend to install them manually. I need some help in this respect.

First with glibc:
In the 'install' file, this is written:
```
GNU libc can be compiled in the source directory, but we strongly advise
building it in a separate build directory.  For example, if you have
unpacked the glibc sources in `/src/gnu/glibc-2.3', create a directory
`/src/gnu/glibc-build' to put the **object files** in.  This allows
removing the whole build directory in case an error occurs, which is the
safest way to get a fresh start and should always be done.

   From your object directory, run the shell script `configure' located
at the top level of the source tree.  In the scenario above, you'd type

     $ ../glibc-2.3/configure ARGS...

   Please note that even if you're building in a separate build
directory, the compilation needs to modify a few files in the source
directory, especially some files in the manual subdirectory.
```
But what the hell are the object files?

---

