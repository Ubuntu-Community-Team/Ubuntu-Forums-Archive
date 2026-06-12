---
title: "Problem compiling ALSA driver"
date: 2008-07-26
forum: General Help
---

### Post by 2WeekHeadache on 2008-07-26
I'm a relative new-comer to the Linux world, but I've been through several distros in the last couple weeks trying to get my wireless cards working.  I finally settled back on Ubuntu since it installed the wireless the easiest, however, now I have no sound.

I will attach the relevant info below, but this machine is an old Gateway Solo 1450 with ESS 1988 Allegro/Maestro sound.  My research indicates that this is supported by the ALSA driver that I have to compile myself (I found nothing in the Package Manager).  When I attempt to compile I get the error highlighted below.  I've found a couple references to the error on Google, but no solutions except for one that was posted as being a "possible / but my fry your install".

[COLOR="Blue"]config.status: include/autoconf-extra.h is unchanged
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
ln: creating symbolic link `include/sound': Permission denied
make: *** [include/sound/version.h] Error 1
[/COLOR]

Any help getting this resolved would be much appreciated.

LSPCI:
[COLOR="Blue"]andy@Solo:/usr/src/alsa/alsa-driver-1.0.9rc4a$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
01:05.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
01:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface[/COLOR]

Full Compile command and output:

[COLOR="Blue"]andy@Solo:/usr/src/alsa/alsa-driver-1.0.9rc4a$ sudo ./configure --with-cards=maestro3 --with-sequencer=yes ; make ; make install
[sudo] password for andy: 
checking for gcc... gcc
checking for C compiler default output... a.out
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.9rc4a
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.24-19-generic/build
checking for directory with kernel build... 
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "no"
checking for existing ALSA module... "no"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "no"
checking for kernel linux/compiler.h... "yes"
checking for kernel linux/pm.h... "yes"
checking for kernel linux/spinlock.h... "yes"
checking for kernel linux/irq.h... "yes"
checking for kernel linux/threads.h... "yes"
checking for kernel linux/rwsem.h... "yes"
checking for kernel linux/gameport.h... "yes"
checking for kernel linux/devfs_fs_kernel.h... "no"
checking for kernel linux/highmem.h... "yes"
checking for kernel linux/workqueue.h... "yes"
checking for kernel linux/dma-mapping.h... "yes"
checking for kernel asm/hw_irq.h... "yes"
checking for kernel linux/device.h... "yes"
checking for kernel linux/jiffies.h... "yes"
checking for kernel linux/compat.h... "yes"
checking for kernel linux/adb.h... "yes"
checking for kernel linux/cuda.h... "yes"
checking for kernel linux/pmu.h... "yes"
checking for kernel linux/moduleparam.h... "yes"
checking for kernel linux/syscalls.h... "yes"
checking for kernel linux/firmware.h... "yes"
checking for exported symbol dump_stack... grep: /lib/modules/2.6.24-19-generic/build/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "yes"
checking for PCI support in kernel... "yes"
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... i586
checking for SMP... "yes"
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... "yes"
checking for strlcpy... "no"
checking for snprintf... "no"
checking for vsnprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for pci_dev_present... "no"
checking for msleep... "no"
checking for tty->count is the atomic type... "no"
checking for io_remap_pfn_range... "no"
checking for new io_remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
checking for driver version... 1.0.9rc4a
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for HPET support... "yes"
checking for Procfs support... "yes"
checking for USB support... "yes"
checking for PC-Speaker hook... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "yes"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "yes"
checking for which soundcards to compile driver for... maestro3
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
ln: creating symbolic link `include/sound': Permission denied
make: *** [include/sound/version.h] Error 1
rm -f /lib/modules/0.0.0/misc/snd*.*o /lib/modules/0.0.0/misc/persist.o /lib/modules/0.0.0/misc/isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
mkdir -p /lib/modules/0.0.0/misc
mkdir: cannot create directory `/lib/modules/0.0.0': Permission denied
make[1]: *** [_modinst__] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [install-modules] Error 1
[/COLOR]

---

### Post by NicoAdamo on 2009-01-18
I'm having at the moment the same error compiling. It's because you triggered a "sudo ./configure [optional_parameters] && make". The problem lays around the "sudo" : it's just for ./configure and not for the make command. Try sudo ./configure [...] && sudo make.

---

