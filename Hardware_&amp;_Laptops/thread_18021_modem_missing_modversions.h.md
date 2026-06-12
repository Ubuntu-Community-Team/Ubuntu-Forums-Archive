---
title: "modem: missing modversions.h"
date: 2005-03-04
forum: Hardware &amp; Laptops
---

### Post by vale on 2005-03-04
Hi everyone!
I've recentcly installed UBUNTU on my laptop (compaq presario x1000) and I'd like to use also  the modem (Agere AC'97)
 I tryed to do the same things I did when I had REDHAT9 where it worked:I use slmdm-2.7.10, but I have some problem compiling.
I downloaded linux-headers but there is not modversions.h
Why? What can I do?
 :confused: When I do "make" I got the follow error:

gcc -Wall -O3 -fomit-frame-pointer -D__KERNEL__ -DMODULE -DEXPORT_SYMTAB -I. -I/usr/src/linux-headers-2.6.8.1-3-386/include  -DMODVERSIONS --include /usr/src/linux-headers-2.6.8.1-3-386/include/linux/modversions.h -o amrmo_init.o -c amrmo_init.c
<command line>:138473835:61872: /usr/src/linux-headers-2.6.8.1-3-386/include/linux/modversions.h: No such file or directory

Thanks 
  Vale

---

### Post by vale on 2005-03-04
Another thing that could be correlated:
I'm also tryng to install the driver for my ADSL USB Modem and when I do "make" there is another missing file: irq_vectors.h...
What do I need to get these files?

cheers
Vale

---

### Post by az on 2005-03-04
install build-essential.

---

### Post by alastair on 2005-03-04
You need to make sure you have the kernel headers installed e.g.

linux-headers-<kernel version>

Check they are installed via synaptic.

Note - slmodem is also available as a package that /might/ work for you.

sl-modem-daemon
sl-modem-source

Read any "readme" under /usr/share/doc/sl-modem*

---

