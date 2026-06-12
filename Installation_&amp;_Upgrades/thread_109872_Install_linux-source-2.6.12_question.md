---
title: "Install linux-source-2.6.12 question"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by ephman on 2005-12-29
hi,

ok i installed linux-source-2.6.12 through the synaptic package manager, and i have a couple questions.

is there anything afterwards i need to do to install the source?

where is the source installed to?

thanks for the bandwidth,
ephman

---

### Post by az on 2005-12-29
You need build-essential to compile stuff.  You should make use of kernel-package to compile and package your custom kernel for easy and safe instalation and removal.

You need gcc-3.4 to compile the 2.6.12 kernel AFAIK.  The default breezy compiler on the install cd is gcc-4.0

The source is in a bzipped tarball in /usr/src

cd /usr/src
tar xvjf linux-source-2.6.12
cd linux-source*
you can then copy your config from /boot/config-2.6.12-10-386 (or whatever)

patch (as needed) config and compile your kernel.

there is a wiki page for using kernel-package.

---

