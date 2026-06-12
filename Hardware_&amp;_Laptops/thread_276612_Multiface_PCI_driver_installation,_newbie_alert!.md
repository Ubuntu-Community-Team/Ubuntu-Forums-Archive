---
title: "Multiface PCI driver installation, newbie alert!"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by agrimur on 2006-10-13
Hi, I am trying to get my RME multiface PCI card to play nice with Ubuntu but have hit a brick wall.  I was following the directions on the [offical alsa project page]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=RME&card=Hammerfall+DSP+9652.&chip=FPGA&module=hdsp") and was trying to compile the driver (note that I am new at linux and barely know what compiling means...) and got the following response:

```
maxicon@maxicon-desktop:/usr/src/alsa/alsa-driver-1.0.13rc3$ sudo ./configure --with-cards=hdsp --with-sequencer=yes;make;make install
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.13rc3
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
bash: make: command not found
bash: make: command not found
```


"...full kernel sources for your distribution..."!?! I am so far from knowing what this means it's not even funny.  I was hoping someone here could point me in the right direction.  Thanks in advance.

AG

---

