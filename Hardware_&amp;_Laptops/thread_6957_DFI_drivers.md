---
title: "DFI drivers"
date: 2004-12-02
forum: Hardware &amp; Laptops
---

### Post by peter_barb on 2004-12-02
I have a DFI lanparty mobo with nforce 2. I went to the nvidia website and downloaded the latest drivers. I am now getting an error with my kernal.

It says. >   ERROR: Unable to find the kernel source tree for the currently running kernel.  Please make sure you have installed the kernel source files for your
         kernel; on Red Hat Linux systems, for example, be sure you have the 'kernel-source' rpm installed.  If you know the correct kernel source files are
         installed, you may specify the kernel source path with the '--kernel-source-path' commandline option.


---

### Post by lagartija on 2004-12-03
to build the driver from nvidia try to install the linux-source package (you have to extract the installed tar files link the new directory to /usr/src/linux) and the header files for the kernel you are using
for me it works
my board is an ABIT AN7 with nforce2 chipset
for example, i use the kernel from the package linux-image-k7-2.6.8.13
and the i've look for and install with synaptic the kernel-headers for the same version

therefore using this drivers you will probably run into problems
it contains only ethernet and sound
you should have already ethernet working and regarding the sound i've found some problem with mplayer and the mixer didn't work for SPDIF
further, your setting are lose at every boot
probably is better that you try to tweak the ALSA driver already contained in ubuntu... (I'm try to understand how switch back to the ALSA drivers...)

bye

---

