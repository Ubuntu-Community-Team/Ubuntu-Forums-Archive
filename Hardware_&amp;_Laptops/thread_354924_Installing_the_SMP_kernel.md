---
title: "Installing the SMP kernel"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by grado on 2007-02-06
Hello Ubunters,

I have 2.6.17-10-386 installed on my centrino duo thinkpad and want to install linux-686-smp package. Synaptic description for linux-686-smp says "Obsoleted by: linux-image-generic". Should I be installing linux-image-generic instead?

Also, I read elsewhere in this forum that installing the smp package made the system unstable. Is it true?

Thanks in advance!

---

### Post by deanjm1963 on 2007-02-06
The "generic-686" kernel has inbuilt smp support for processors that support it so install the generic-686 kernel.

---

### Post by grado on 2007-02-09
Thanks dean! Installed the smp package and now I can see two cpus in /proc/cpuinfo.
But as a result of this, my display is slow than it used to be and Beryl crashed for no real reson.

Thanks!

---

### Post by Temujin_12 on 2007-03-29
I had the same problem.  The 386 kernel, which was the default one that came along with Edgy, was only showing 1 CPU for my P4 3.0 GHz that has hyperthreading.  I installed (apt-get) 'linux-image-generic' which gave me an additional 'generic' kernel option in GRUB.  Booting to that one, I now see two CPUs in /proc/cpuinfo.

FYI, you'll need to set the 'generic' kernel GRUB option to be the default otherwise it will fall back to the 386 kernel option on next boot (edit '/boot/grub/menu.lst' to do so).

---

### Post by grado on 2007-03-30
Thats true but but my beryl window manager seems to crash with any of the smp kernels and works only for the 386 image.

---

