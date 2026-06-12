---
title: "Creative X-Fi &amp; Installing Driver"
date: 2008-06-07
forum: Hardware
---

### Post by MechWarrior001 on 2008-06-07
I'm trying to install the (Linux) Driver for my Creative X-Fi Fatality Card and this is what I get in Terminal:

```
Installation is in progress. Please wait...
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful
```

How do you solve this?

---

### Post by Nepherte on 2008-06-07
You checked the config.log file? What's in it?

---

### Post by MechWarrior001 on 2008-06-07
Umm... where is it? Like what folder is it in?

---

### Post by Nepherte on 2008-06-07
Most likely in the directory you tryed to compile it.

---

### Post by MechWarrior001 on 2008-06-07
Uh nope its not there.

---

### Post by zole052 on 2008-06-12
> **MechWarrior001 said:**
> I'm trying to install the (Linux) Driver for my Creative X-Fi Fatality Card and this is what I get in Terminal:

```
Installation is in progress. Please wait...
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful
```

How do you solve this?

install libc6-dev!

write in terminal "sudo apt-get install libc6-dev gcc build-essential binutils-dev"

you solve the first problem. now when i try to install x-fi drivers i get:

Installation is in progress. Please wait...
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
checking for current directory... /opt/Creative/XFiDrv_Linux_US-1.18/drivers
checking cross compile...
checking for directory with kernel source... /lib/modules/2.6.24-18-generic/build
checking for directory with kernel build...
checking for directory with ALSA include files... /lib/modules/2.6.24-18-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-18-generic
checking for GCC version... Kernel compiler: Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... no
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.24-18-generic/kernel/sound
checking for ISA support in kernel... yes
checking for processor type... i586
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for Procfs support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new unlocked/compat_ioctl... no
configure: creating ./config.status
config.status: creating Makefile.conf
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful

someone help :)

---

### Post by MechWarrior001 on 2008-06-12
Ok this is pissing me off. I did type the *sudo apt-get* stuff in terminal and ran the ./configure script, but now I can't hear any audio from Wine, Tremulous, or PCSX. Worse, I don't know where to find the files and delete them to get Audio back. What do I do now?

EDIT: Now when I try to play Vendetta Online, I don't get any sound what-so-ever and now my ALSA Driver Doesn't show up in the Driver Selection Menu.

Any help?

---

