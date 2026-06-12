---
title: "Soundblaster X-FI Xtremegamer"
date: 2008-09-21
forum: Hardware
---

### Post by Nettoyer on 2008-09-21
Edit:  I followed this guide here: [http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_218.html]("http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_218.html")

Step 1: Reboot computer
Step 2: At the GDM, Press CTRL+ALT+F1 (Should be at Term 1)
Step 3: go to the location of your oss file and run it
Step 4: Execute: sudo dpkg --install oss-linux-4.1-rc1_amd64.deb / see above.
Step 5: Look at guide and hopefully it works for you.

Kernel: 2.6.24-19-generic
Ver:  Ubuntu 8.04 LTS Hardy

I ran the install on this package for my soundcard and this is what I get:
```
 sudo dpkg --install oss-linux-4.1-rc1_amd64.deb
(Reading database ... 113762 files and directories currently installed.)
Preparing to replace oss-linux 4.1-rc1 (using oss-linux-4.1-rc1_amd64.deb) ...
OSS not loaded.
 * Shutting down ALSA...                                                                                                                                                 [ OK ] 
Unpacking replacement oss-linux ...
Upgrading OSS - will not purge /usr/lib/oss.
Setting up oss-linux (4.1-rc1) ...
Building OSS Modules for Linux-unknown 2.6.24-19-generic

OSS build environment set up for REGPARM kernels

Building module osscore
Building module oss_ali5455
Building module oss_atiaudio
Building module oss_audigyls
Building module oss_audioloop
Building module oss_audiopci
Building module oss_cmi878x
Building module oss_cmpci
Building module oss_cs4281
Building module oss_cs461x
Building module oss_digi96
Building module oss_emu10k1x
Building module oss_envy24
Building module oss_envy24ht
Building module oss_fmedia
Building module oss_geode
Building module oss_hdaudio
Building module oss_ich
Building module oss_imux
Building module oss_midiloop
Building module oss_midimix
Building module oss_sblive
Building module oss_sbpci
Building module oss_sbxfi
Building module oss_solo
Building module oss_trident
Building module oss_usb
Building module oss_userdev
Building module oss_via823x
Building module oss_via97
Building module oss_ymf7xx
depmod -a
Forcing re-detection of installed soundcards
Starting Open Sound System
mv: cannot move `/dev/snd' to `/dev/snd.osssave/snd': Directory not empty
ERROR: Module snd_intel8x0 is in use
ERROR: Module snd_ac97_codec is in use by snd_intel8x0
ERROR: Module snd_pcm is in use by snd_intel8x0,snd_ac97_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_intel8x0,snd_pcm
ERROR: Module snd_intel8x0 is in use
ERROR: Module snd_ac97_codec is in use by snd_intel8x0
ERROR: Module snd_pcm is in use by snd_intel8x0,snd_ac97_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_intel8x0,snd_pcm
ERROR: Module snd_intel8x0 is in use
ERROR: Module snd_ac97_codec is in use by snd_intel8x0
ERROR: Module snd_pcm is in use by snd_intel8x0,snd_ac97_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_intel8x0,snd_pcm
ERROR: Module snd_intel8x0 is in use
ERROR: Module snd_ac97_codec is in use by snd_intel8x0
ERROR: Module snd_pcm is in use by snd_intel8x0,snd_ac97_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_intel8x0,snd_pcm
ERROR: Module snd_intel8x0 is in use
ERROR: Module snd_ac97_codec is in use by snd_intel8x0
ERROR: Module snd_pcm is in use by snd_intel8x0,snd_ac97_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_intel8x0,snd_pcm
ERROR: Module snd_intel8x0 is in use
ERROR: Module snd_ac97_codec is in use by snd_intel8x0
ERROR: Module snd_pcm is in use by snd_intel8x0,snd_ac97_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_intel8x0,snd_pcm
ERROR: Module snd_intel8x0 is in use
ERROR: Module snd_ac97_codec is in use by snd_intel8x0
ERROR: Module snd_pcm is in use by snd_intel8x0,snd_ac97_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_intel8x0,snd_pcm
ERROR: Module snd_intel8x0 is in use
ERROR: Module snd_ac97_codec is in use by snd_intel8x0
ERROR: Module snd_pcm is in use by snd_intel8x0,snd_ac97_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_intel8x0,snd_pcm
ERROR: Module snd_intel8x0 is in use
ERROR: Module snd_ac97_codec is in use by snd_intel8x0
ERROR: Module snd_pcm is in use by snd_intel8x0,snd_ac97_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_intel8x0,snd_pcm
ERROR: Module snd_intel8x0 is in use
ERROR: Module snd_ac97_codec is in use by snd_intel8x0
ERROR: Module snd_pcm is in use by snd_intel8x0,snd_ac97_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_intel8x0,snd_pcm
ERROR: Module snd_intel8x0 is in use
ERROR: Module snd_ac97_codec is in use by snd_intel8x0
ERROR: Module snd_pcm is in use by snd_intel8x0,snd_ac97_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_intel8x0,snd_pcm
Failed to disable conflicting sound drivers
Reboot and try running soundon again

Also check that you have not compiled sound support statically
into the kernel.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```
Maybe if I can make the module not in use... ?
I know that I have onboard audio and my X-FI Card (I'd prefer the XFI)
I also tried downloading & installing that 64bit linux driver from Creative.

```
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
checking for directory with kernel source... /lib/modules/2.6.24-19-generic/build
checking for directory with kernel build... 
checking for directory with ALSA include files... /lib/modules/2.6.24-19-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-19-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

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
checking for directory to store kernel modules... /lib/modules/2.6.24-19-generic/kernel/sound
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for ISA DMA API... yes
checking for 32bit compat support... yes
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

```

```

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at c800 [size=256]
	I/O ports at c400 [size=256]
	Memory at f7ffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>


01:07.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Unknown device 0031
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at dc00 [size=32]
	Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

```
The top is my onboard audio which was working and then my SB card.

---

### Post by markbuntu on 2008-09-21
Temujin has written instructions for installing OSS4 on Ubuntu Hardy here:


[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

---

