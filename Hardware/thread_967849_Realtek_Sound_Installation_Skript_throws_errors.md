---
title: "Realtek Sound Installation Skript throws errors"
date: 2008-11-02
forum: Hardware
---

### Post by JohannesD on 2008-11-02
Hi,
I'm new to this forum and hope, someone can help.

I updated from 8.04 to 8.10. When I realized, that the sound doesn't work, I tried to reinstall the driver (official driver of Realtek) by executing the install skript. Unfortunately, there are come some errors... Here is the output:

```
johannes@johann-4:~/Desktop/realtek-linux-audiopack-5.07$ sudo ./install
[sudo] password for johannes: 
.....Decompress Driver source v1.0.17-5.07
.....Decompress ALSA Library source v1.0.16
.....Decompress ALSA Utility v1.0.16
Remove old sound driver
Compile Driver........
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.27-7-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.27-7-generic
[color=#DA0000]checking for GCC version... ./configure: eval: line 5057: syntax error near unexpected token `)'[/color]
./configure: eval: line 5057: `my_compiler_version=4.3.2-1ubuntu11)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.2-1ubuntu11) 4.3.2

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
Removing a dummy media/v4l2-dev.h.
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos_params.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker input subsystem in kernel... module
checking for directory to store kernel modules... /lib/modules/2.6.27-7-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.17
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... yes
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... hda-intel
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
make dep
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #2 succeeded at 156 (offset -1 lines).
Hunk #3 succeeded at 168 (offset -1 lines).
Hunk #4 succeeded at 178 (offset -1 lines).
Hunk #5 succeeded at 209 (offset -1 lines).
Hunk #6 succeeded at 494 (offset -1 lines).
Hunk #7 succeeded at 534 with fuzz 2 (offset -1 lines).
Hunk #8 succeeded at 993 (offset -1 lines).
Hunk #9 succeeded at 1022 (offset -1 lines).
copying file alsa-kernel/core/pcm.c
patching file pcm.c
Hunk #2 succeeded at 898 (offset -12 lines).
Hunk #3 succeeded at 914 (offset -12 lines).
Hunk #4 succeeded at 926 (offset -12 lines).
Hunk #5 succeeded at 980 (offset -12 lines).
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #4 succeeded at 1585 (offset -17 lines).
Hunk #5 succeeded at 2820 (offset -39 lines).
Hunk #6 succeeded at 2840 (offset -39 lines).
Hunk #7 succeeded at 2870 (offset -39 lines).
Hunk #8 succeeded at 2897 (offset -39 lines).
Hunk #9 succeeded at 2913 (offset -39 lines).
Hunk #10 succeeded at 2943 (offset -39 lines).
Hunk #11 succeeded at 3029 (offset -39 lines).
Hunk #12 succeeded at 3048 (offset -39 lines).
Hunk #13 succeeded at 3062 (offset -39 lines).
Hunk #14 succeeded at 3120 (offset -39 lines).
Hunk #15 succeeded at 3148 (offset -39 lines).
Hunk #16 succeeded at 3206 (offset -39 lines).
Hunk #17 succeeded at 3235 (offset -39 lines).
Hunk #18 succeeded at 3265 (offset -39 lines).
Hunk #19 succeeded at 3342 (offset -39 lines).
Hunk #20 succeeded at 3374 (offset -39 lines).
Hunk #21 succeeded at 3440 (offset -39 lines).
Hunk #22 succeeded at 3469 (offset -39 lines).
Hunk #23 succeeded at 3510 (offset -39 lines).
Hunk #24 succeeded at 3660 (offset -39 lines).
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #3 succeeded at 713 (offset -6 lines).
Hunk #4 succeeded at 776 (offset -10 lines).
Hunk #5 succeeded at 1384 (offset -10 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/init.c
patching file init.c
Hunk #2 succeeded at 277 (offset 13 lines).
Hunk #3 succeeded at 303 (offset 13 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #3 succeeded at 1291 (offset 2 lines).
Hunk #4 succeeded at 1375 (offset 2 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #3 succeeded at 990 (offset -2 lines).
Hunk #4 succeeded at 1912 (offset -2 lines).
Hunk #5 succeeded at 1957 (offset -2 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
copying file alsa-kernel/core/misc.c
patching file misc.c
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/ioctl32'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/ioctl32'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #3 succeeded at 2589 (offset -1 lines).
Hunk #4 succeeded at 2640 (offset -1 lines).
Hunk #5 succeeded at 2763 (offset -1 lines).
Hunk #6 succeeded at 2946 (offset -1 lines).
Hunk #7 succeeded at 3073 (offset -1 lines).
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/oss'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
make[4]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
make[4]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/seq/oss'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/seq'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/i2c'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/i2c/l3'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/i2c/l3'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/i2c/other'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/i2c/other'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/i2c'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers'
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers/mpu401'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers/opl3'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers/opl4'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers/opl4'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers/pcsp'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers/pcsp'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers/vx'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers/vx'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/drivers'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/ad1816a'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/ad1816a'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/ad1848'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/ad1848'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/cs423x'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/cs423x'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/es1688'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/es1688'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/gus'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/gus'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/msnd'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/msnd'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/opti9xx'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/opti9xx'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/sb'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
copying file alsa-kernel/isa/wavefront/wavefront_synth.c
patching file wavefront_synth.c
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa/wavefront'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/isa'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/synth'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/synth/emux'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/synth/emux'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/synth'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
copying file alsa-kernel/pci/atiixp.c
patching file atiixp.c
Hunk #2 succeeded at 1668 (offset -3 lines).
Hunk #3 succeeded at 1713 (offset -3 lines).
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c
Hunk #2 succeeded at 1309 (offset 2 lines).
Hunk #3 succeeded at 1352 (offset 2 lines).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #2 succeeded at 844 (offset -2 lines).
Hunk #3 succeeded at 998 (offset -2 lines).
copying file alsa-kernel/pci/cmipci.c
patching file cmipci.c
Hunk #2 succeeded at 3131 (offset -45 lines).
Hunk #3 succeeded at 3426 (offset -45 lines).
copying file alsa-kernel/pci/ens1370.c
patching file ens1370.c
Hunk #2 succeeded at 2119 (offset -12 lines).
Hunk #3 succeeded at 2495 (offset -12 lines).
copying file alsa-kernel/pci/fm801.c
patching file fm801.c
Hunk #2 succeeded at 1426 (offset 23 lines).
Hunk #3 succeeded at 1607 (offset 23 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #5 succeeded at 3133 (offset 5 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #2 succeeded at 2755 (offset 10 lines).
Hunk #3 succeeded at 2943 (offset 12 lines).
copying file alsa-kernel/pci/via82xx.c
patching file via82xx.c
Hunk #2 succeeded at 2439 (offset 3 lines).
Hunk #3 succeeded at 2449 (offset 3 lines).
Hunk #4 succeeded at 2464 (offset 3 lines).
Hunk #5 succeeded at 2475 (offset 3 lines).
Hunk #6 succeeded at 2486 (offset 3 lines).
Hunk #7 succeeded at 2569 (offset 3 lines).
copying file alsa-kernel/pci/via82xx_modem.c
patching file via82xx_modem.c
Hunk #2 succeeded at 1182 (offset 2 lines).
Hunk #3 succeeded at 1242 (offset 2 lines).
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #3 succeeded at 1912 (offset 1 line).
Hunk #4 succeeded at 1924 (offset 1 line).
Hunk #5 succeeded at 1948 (offset 1 line).
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/ac97'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/ali5451'
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c
Hunk #2 succeeded at 2207 (offset 2 lines).
Hunk #3 succeeded at 2377 (offset 2 lines).
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/ali5451'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/asihpi'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/asihpi'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/au88x0'
copying file alsa-kernel/pci/au88x0/au88x0.c
patching file au88x0.c
Hunk #2 succeeded at 340 (offset -1 lines).
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/au88x0'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/aw2'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/aw2'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/ca0106'
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c
Hunk #3 succeeded at 1365 (offset 12 lines).
Hunk #4 succeeded at 1734 (offset 12 lines).
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/ca0106'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/cs46xx'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/cs46xx'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/cs5535audio'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/cs5535audio'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1898 (offset -28 lines).
Hunk #2 succeeded at 1961 (offset -28 lines).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/echoaudio'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #4 succeeded at 1406 (offset 1 line).
Hunk #5 succeeded at 1447 (offset 9 lines).
Hunk #6 succeeded at 1756 (offset 10 lines).
copying file alsa-kernel/pci/emu10k1/emu10k1x.c
patching file emu10k1x.c
Hunk #2 succeeded at 942 (offset 2 lines).
Hunk #3 succeeded at 1630 (offset 2 lines).
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/emu10k1'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
Hunk #2 succeeded at 311 (offset 32 lines).
Hunk #3 succeeded at 349 (offset 32 lines).
Hunk #4 succeeded at 364 (offset 32 lines).
Hunk #5 succeeded at 380 (offset 32 lines).
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/hda'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/ice1712'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/ice1712'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #2 succeeded at 2352 (offset 3 lines).
Hunk #3 succeeded at 2513 (offset 3 lines).
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/korg1212'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/mixart'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/mixart'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/nm256'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/nm256'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/oxygen'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/oxygen'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/pcxhr'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/pcxhr'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/pdplus'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/pdplus'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #3 succeeded at 2236 (offset 2 lines).
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/riptide'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/rme9652'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/rme9652'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/trident'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/trident'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/vx222'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/vx222'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
Hunk #2 succeeded at 2049 (offset 5 lines).
Hunk #3 succeeded at 2071 (offset 5 lines).
Hunk #4 succeeded at 2413 (offset 7 lines).
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci/ymfpci'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pci'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa/codecs'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa/codecs'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa/core'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa/core'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa/fabrics'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa/fabrics'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa/soundbus'
make[4]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa/soundbus/i2sbus'
make[4]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa/soundbus/i2sbus'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa/soundbus'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/aoa'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/at32'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/at32'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/at91'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/at91'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/au1x'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/au1x'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/codecs'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/codecs'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/davinci'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/davinci'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/fsl'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/fsl'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/omap'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/omap'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/pxa'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/pxa'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/s3c24xx'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/s3c24xx'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/sh'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc/sh'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/soc'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #2 succeeded at 70 with fuzz 2.
Hunk #3 succeeded at 686 (offset 27 lines).
Hunk #4 succeeded at 713 (offset 27 lines).
Hunk #5 succeeded at 794 with fuzz 2 (offset 27 lines).
Hunk #6 succeeded at 809 with fuzz 2 (offset 27 lines).
Hunk #7 succeeded at 1183 with fuzz 1 (offset 23 lines).
Hunk #8 succeeded at 2112 (offset 30 lines).
Hunk #9 succeeded at 2131 (offset 30 lines).
Hunk #10 succeeded at 2143 (offset 30 lines).
Hunk #11 succeeded at 2156 (offset 30 lines).
Hunk #12 succeeded at 2736 (offset 49 lines).
Hunk #13 succeeded at 2808 (offset 49 lines).
Hunk #14 succeeded at 3096 (offset 49 lines).
Hunk #15 succeeded at 3167 (offset 49 lines).
Hunk #16 succeeded at 3288 (offset 49 lines).
Hunk #17 succeeded at 3306 (offset 49 lines).
Hunk #18 succeeded at 3320 (offset 49 lines).
Hunk #19 succeeded at 3333 (offset 49 lines).
Hunk #20 succeeded at 3536 (offset 48 lines).
Hunk #21 succeeded at 3629 (offset 48 lines).
Hunk #22 succeeded at 3767 (offset 49 lines).
Hunk #23 succeeded at 3828 (offset 49 lines).
Hunk #24 succeeded at 3847 (offset 49 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 227 (offset 2 lines).
Hunk #3 succeeded at 251 (offset 2 lines).
Hunk #4 succeeded at 350 (offset 8 lines).
Hunk #5 succeeded at 1465 (offset 103 lines).
Hunk #6 succeeded at 1814 (offset 108 lines).
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/usb/caiaq'
copying file alsa-kernel/usb/caiaq/caiaq-audio.c
patching file caiaq-audio.c
Hunk #1 succeeded at 1 with fuzz 2.
Hunk #2 succeeded at 448 with fuzz 1 (offset -13 lines).
Hunk #3 succeeded at 511 (offset -8 lines).
copying file alsa-kernel/usb/caiaq/caiaq-device.c
patching file caiaq-device.c
Hunk #2 succeeded at 120 (offset 6 lines).
Hunk #3 succeeded at 370 (offset 6 lines).
copying file alsa-kernel/usb/caiaq/caiaq-input.c
patching file caiaq-input.c
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/usb/caiaq'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #11 succeeded at 1057 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/usb/usx2y'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/usb'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pcmcia'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pcmcia/pdaudiocf'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pcmcia/pdaudiocf'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pcmcia/vx'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pcmcia/vx'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/pcmcia'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07'
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07  CPP="gcc -E" CC="gcc" modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/hwdep.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/memory_wrapper.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/memalloc.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/sgbuf.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/pcm.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/pcm_native.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/pcm_lib.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/pcm_timer.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/pcm_misc.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/pcm_memory.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/timer.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/wrappers.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/misc_driver.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/sound.o
/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/sound.c: In Funktion »snd_request_other«:
/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/sound.c:100: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/init.o
/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/init.c: In Funktion »snd_card_register«:
/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/init.c:568: Warnung: Übergabe des Arguments 5 von »device_create« erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/init.c:568: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/memory.o
  CC [M]  /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/info.o
/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/info.c: In Funktion »resize_info_buffer«:
[color=#DA0000]/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/info.c:90: Fehler: Implizite Deklaration der Funktion »PAGE_ALIGN«[/color]
make[3]: *** [/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore/info.o] Fehler 1
make[2]: *** [/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore] Fehler 2
make[1]: *** [_module_/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.27-7-generic'
[color=#DA0000]make: *** [compile] Fehler 2[/color]
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore'
mkdir -p /lib/modules/2.6.27-7-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.27-7-generic/kernel/sound/acore
[color=#DA0000]cp: Aufruf von stat für „snd-hwdep.ko“ nicht möglich: No such file or directory
cp: Aufruf von stat für „snd-page-alloc.ko“ nicht möglich: No such file or directory
cp: Aufruf von stat für „snd-pcm.ko“ nicht möglich: No such file or directory
cp: Aufruf von stat für „snd-timer.ko“ nicht möglich: No such file or directory
cp: Aufruf von stat für „snd.ko“ nicht möglich: No such file or directory
make[1]: *** [modules_install] Fehler 1[/color]
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-driver-1.0.17-5.07/acore'
[color=#DA0000]make: *** [install-modules] Fehler 1[/color]
Creating mixer?...done.
Creating sequencer...done.
Creating midi0?...done.
Creating dsp?...done.
Creating audio?...done.
Creating sndstat...done.
Creating music...done.
Creating dmmidi?...done.
Creating dmfm?...done.
Creating amixer?...done.
Creating adsp?...done.
Creating amidi?...done.
Creating admmidi?...done.
[color=#DA0000]rm: Entfernen von „/dev/snd“ nicht möglich: Is a directory[/color]
Creating snd/control?...done.
Creating snd/seq...done.
Creating snd/timer...done.
Creating snd/hw??...done.
Creating snd/midi??...done.
Creating snd/pcm??p...done.
Creating snd/pcm??c...done.
Creating aload?...done.
Creating aloadSEQ...done.
Remove old alsa library
Compile ALSA Library.....
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for hsearch_r... yes
checking for library version... major 1 minor 0 subminor 16 extrastr  extraver 1000000
checking for versioned symbols... yes
checking for symbolic-functions... no
checking for custom symbol prefixes... 
checking for debug... yes
checking for debug assert... no
checking for tmpdir... /tmp
checking for softfloat... no
checking for libdl... checking for dlsym in -ldl... yes
checking for pthread... checking for pthread_join in -lpthread... yes
checking for librt... checking for clock_gettime in -lrt... yes
checking for architecture... x86
checking wordexp.h usability... yes
checking wordexp.h presence... yes
checking for wordexp.h... yes
checking for resmgr support... no
checking for aload* support... yes
checking for ALSA device file directory... /dev/snd/
checking for aload* device file directory... /dev/
[color=#DA0000]./configure: line 21666: python-config: command not found
./configure: line 21674: python-config: command not found
Unable to determine python libraries! Probably python-config is not
available on this system. Please, use --with-pythonlibs and
--with-pythonincludes options. Python components are disabled in this build.[/color]
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating doc/pictures/Makefile
config.status: creating include/Makefile
config.status: creating include/sound/Makefile
config.status: creating src/Versions
config.status: creating src/Makefile
config.status: creating src/control/Makefile
config.status: creating src/mixer/Makefile
config.status: creating src/pcm/Makefile
config.status: creating src/pcm/scopes/Makefile
config.status: creating src/rawmidi/Makefile
config.status: creating src/timer/Makefile
config.status: creating src/hwdep/Makefile
config.status: creating src/seq/Makefile
config.status: creating src/compat/Makefile
config.status: creating src/alisp/Makefile
config.status: creating src/conf/Makefile
config.status: creating src/conf/cards/Makefile
config.status: creating src/conf/pcm/Makefile
config.status: creating modules/Makefile
config.status: creating modules/mixer/Makefile
config.status: creating modules/mixer/simple/Makefile
config.status: creating alsalisp/Makefile
config.status: creating aserver/Makefile
config.status: creating test/Makefile
config.status: creating utils/Makefile
config.status: creating utils/alsa-lib.spec
config.status: creating utils/alsa.pc
config.status: creating include/config.h
config.status: executing depfiles commands
Creating asoundlib.h...
Making all in doc
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc'
Making all in pictures
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc/pictures'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc/pictures'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc'
make[2]: Für das Ziel »all-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc'
Making all in include
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
make  all-recursive
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
Making all in sound
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include/sound'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include/sound'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
Making all in src
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src'
Making all in control
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/control'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT cards.lo -MD -MP -MF ".deps/cards.Tpo" -c -o cards.lo cards.c; \
	then mv -f ".deps/cards.Tpo" ".deps/cards.Plo"; else rm -f ".deps/cards.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT cards.lo -MD -MP -MF .deps/cards.Tpo -c cards.c  -fPIC -DPIC -o .libs/cards.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT tlv.lo -MD -MP -MF ".deps/tlv.Tpo" -c -o tlv.lo tlv.c; \
	then mv -f ".deps/tlv.Tpo" ".deps/tlv.Plo"; else rm -f ".deps/tlv.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT tlv.lo -MD -MP -MF .deps/tlv.Tpo -c tlv.c  -fPIC -DPIC -o .libs/tlv.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT namehint.lo -MD -MP -MF ".deps/namehint.Tpo" -c -o namehint.lo namehint.c; \
	then mv -f ".deps/namehint.Tpo" ".deps/namehint.Plo"; else rm -f ".deps/namehint.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT namehint.lo -MD -MP -MF .deps/namehint.Tpo -c namehint.c  -fPIC -DPIC -o .libs/namehint.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT hcontrol.lo -MD -MP -MF ".deps/hcontrol.Tpo" -c -o hcontrol.lo hcontrol.c; \
	then mv -f ".deps/hcontrol.Tpo" ".deps/hcontrol.Plo"; else rm -f ".deps/hcontrol.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT hcontrol.lo -MD -MP -MF .deps/hcontrol.Tpo -c hcontrol.c  -fPIC -DPIC -o .libs/hcontrol.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT control.lo -MD -MP -MF ".deps/control.Tpo" -c -o control.lo control.c; \
	then mv -f ".deps/control.Tpo" ".deps/control.Plo"; else rm -f ".deps/control.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT control.lo -MD -MP -MF .deps/control.Tpo -c control.c  -fPIC -DPIC -o .libs/control.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT control_hw.lo -MD -MP -MF ".deps/control_hw.Tpo" -c -o control_hw.lo control_hw.c; \
	then mv -f ".deps/control_hw.Tpo" ".deps/control_hw.Plo"; else rm -f ".deps/control_hw.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT control_hw.lo -MD -MP -MF .deps/control_hw.Tpo -c control_hw.c  -fPIC -DPIC -o .libs/control_hw.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT setup.lo -MD -MP -MF ".deps/setup.Tpo" -c -o setup.lo setup.c; \
	then mv -f ".deps/setup.Tpo" ".deps/setup.Plo"; else rm -f ".deps/setup.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT setup.lo -MD -MP -MF .deps/setup.Tpo -c setup.c  -fPIC -DPIC -o .libs/setup.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT control_symbols.lo -MD -MP -MF ".deps/control_symbols.Tpo" -c -o control_symbols.lo control_symbols.c; \
	then mv -f ".deps/control_symbols.Tpo" ".deps/control_symbols.Plo"; else rm -f ".deps/control_symbols.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT control_symbols.lo -MD -MP -MF .deps/control_symbols.Tpo -c control_symbols.c  -fPIC -DPIC -o .libs/control_symbols.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT control_shm.lo -MD -MP -MF ".deps/control_shm.Tpo" -c -o control_shm.lo control_shm.c; \
	then mv -f ".deps/control_shm.Tpo" ".deps/control_shm.Plo"; else rm -f ".deps/control_shm.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT control_shm.lo -MD -MP -MF .deps/control_shm.Tpo -c control_shm.c  -fPIC -DPIC -o .libs/control_shm.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT control_ext.lo -MD -MP -MF ".deps/control_ext.Tpo" -c -o control_ext.lo control_ext.c; \
	then mv -f ".deps/control_ext.Tpo" ".deps/control_ext.Plo"; else rm -f ".deps/control_ext.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT control_ext.lo -MD -MP -MF .deps/control_ext.Tpo -c control_ext.c  -fPIC -DPIC -o .libs/control_ext.o
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libcontrol.la   cards.lo tlv.lo namehint.lo hcontrol.lo control.lo control_hw.lo setup.lo control_symbols.lo control_shm.lo control_ext.lo  
ar cru .libs/libcontrol.a .libs/cards.o .libs/tlv.o .libs/namehint.o .libs/hcontrol.o .libs/control.o .libs/control_hw.o .libs/setup.o .libs/control_symbols.o .libs/control_shm.o .libs/control_ext.o
ranlib .libs/libcontrol.a
creating libcontrol.la
(cd .libs && rm -f libcontrol.la && ln -s ../libcontrol.la libcontrol.la)
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/control'
Making all in mixer
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/mixer'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT bag.lo -MD -MP -MF ".deps/bag.Tpo" -c -o bag.lo bag.c; \
	then mv -f ".deps/bag.Tpo" ".deps/bag.Plo"; else rm -f ".deps/bag.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT bag.lo -MD -MP -MF .deps/bag.Tpo -c bag.c  -fPIC -DPIC -o .libs/bag.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT mixer.lo -MD -MP -MF ".deps/mixer.Tpo" -c -o mixer.lo mixer.c; \
	then mv -f ".deps/mixer.Tpo" ".deps/mixer.Plo"; else rm -f ".deps/mixer.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT mixer.lo -MD -MP -MF .deps/mixer.Tpo -c mixer.c  -fPIC -DPIC -o .libs/mixer.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT simple.lo -MD -MP -MF ".deps/simple.Tpo" -c -o simple.lo simple.c; \
	then mv -f ".deps/simple.Tpo" ".deps/simple.Plo"; else rm -f ".deps/simple.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT simple.lo -MD -MP -MF .deps/simple.Tpo -c simple.c  -fPIC -DPIC -o .libs/simple.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT simple_none.lo -MD -MP -MF ".deps/simple_none.Tpo" -c -o simple_none.lo simple_none.c; \
	then mv -f ".deps/simple_none.Tpo" ".deps/simple_none.Plo"; else rm -f ".deps/simple_none.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT simple_none.lo -MD -MP -MF .deps/simple_none.Tpo -c simple_none.c  -fPIC -DPIC -o .libs/simple_none.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT simple_abst.lo -MD -MP -MF ".deps/simple_abst.Tpo" -c -o simple_abst.lo simple_abst.c; \
	then mv -f ".deps/simple_abst.Tpo" ".deps/simple_abst.Plo"; else rm -f ".deps/simple_abst.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT simple_abst.lo -MD -MP -MF .deps/simple_abst.Tpo -c simple_abst.c  -fPIC -DPIC -o .libs/simple_abst.o
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libmixer.la   bag.lo mixer.lo simple.lo simple_none.lo simple_abst.lo  
ar cru .libs/libmixer.a .libs/bag.o .libs/mixer.o .libs/simple.o .libs/simple_none.o .libs/simple_abst.o
ranlib .libs/libmixer.a
creating libmixer.la
(cd .libs && rm -f libmixer.la && ln -s ../libmixer.la libmixer.la)
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/mixer'
Making all in pcm
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/pcm'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/pcm'
make[3]: Für das Ziel »all-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/pcm'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT atomic.lo -MD -MP -MF ".deps/atomic.Tpo" -c -o atomic.lo atomic.c; \
	then mv -f ".deps/atomic.Tpo" ".deps/atomic.Plo"; else rm -f ".deps/atomic.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT atomic.lo -MD -MP -MF .deps/atomic.Tpo -c atomic.c  -fPIC -DPIC -o .libs/atomic.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT mask.lo -MD -MP -MF ".deps/mask.Tpo" -c -o mask.lo mask.c; \
	then mv -f ".deps/mask.Tpo" ".deps/mask.Plo"; else rm -f ".deps/mask.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT mask.lo -MD -MP -MF .deps/mask.Tpo -c mask.c  -fPIC -DPIC -o .libs/mask.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT interval.lo -MD -MP -MF ".deps/interval.Tpo" -c -o interval.lo interval.c; \
	then mv -f ".deps/interval.Tpo" ".deps/interval.Plo"; else rm -f ".deps/interval.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT interval.lo -MD -MP -MF .deps/interval.Tpo -c interval.c  -fPIC -DPIC -o .libs/interval.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm.lo -MD -MP -MF ".deps/pcm.Tpo" -c -o pcm.lo pcm.c; \
	then mv -f ".deps/pcm.Tpo" ".deps/pcm.Plo"; else rm -f ".deps/pcm.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm.lo -MD -MP -MF .deps/pcm.Tpo -c pcm.c  -fPIC -DPIC -o .libs/pcm.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_params.lo -MD -MP -MF ".deps/pcm_params.Tpo" -c -o pcm_params.lo pcm_params.c; \
	then mv -f ".deps/pcm_params.Tpo" ".deps/pcm_params.Plo"; else rm -f ".deps/pcm_params.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_params.lo -MD -MP -MF .deps/pcm_params.Tpo -c pcm_params.c  -fPIC -DPIC -o .libs/pcm_params.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_simple.lo -MD -MP -MF ".deps/pcm_simple.Tpo" -c -o pcm_simple.lo pcm_simple.c; \
	then mv -f ".deps/pcm_simple.Tpo" ".deps/pcm_simple.Plo"; else rm -f ".deps/pcm_simple.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_simple.lo -MD -MP -MF .deps/pcm_simple.Tpo -c pcm_simple.c  -fPIC -DPIC -o .libs/pcm_simple.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_hw.lo -MD -MP -MF ".deps/pcm_hw.Tpo" -c -o pcm_hw.lo pcm_hw.c; \
	then mv -f ".deps/pcm_hw.Tpo" ".deps/pcm_hw.Plo"; else rm -f ".deps/pcm_hw.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_hw.lo -MD -MP -MF .deps/pcm_hw.Tpo -c pcm_hw.c  -fPIC -DPIC -o .libs/pcm_hw.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_misc.lo -MD -MP -MF ".deps/pcm_misc.Tpo" -c -o pcm_misc.lo pcm_misc.c; \
	then mv -f ".deps/pcm_misc.Tpo" ".deps/pcm_misc.Plo"; else rm -f ".deps/pcm_misc.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_misc.lo -MD -MP -MF .deps/pcm_misc.Tpo -c pcm_misc.c  -fPIC -DPIC -o .libs/pcm_misc.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_mmap.lo -MD -MP -MF ".deps/pcm_mmap.Tpo" -c -o pcm_mmap.lo pcm_mmap.c; \
	then mv -f ".deps/pcm_mmap.Tpo" ".deps/pcm_mmap.Plo"; else rm -f ".deps/pcm_mmap.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_mmap.lo -MD -MP -MF .deps/pcm_mmap.Tpo -c pcm_mmap.c  -fPIC -DPIC -o .libs/pcm_mmap.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_symbols.lo -MD -MP -MF ".deps/pcm_symbols.Tpo" -c -o pcm_symbols.lo pcm_symbols.c; \
	then mv -f ".deps/pcm_symbols.Tpo" ".deps/pcm_symbols.Plo"; else rm -f ".deps/pcm_symbols.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_symbols.lo -MD -MP -MF .deps/pcm_symbols.Tpo -c pcm_symbols.c  -fPIC -DPIC -o .libs/pcm_symbols.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_generic.lo -MD -MP -MF ".deps/pcm_generic.Tpo" -c -o pcm_generic.lo pcm_generic.c; \
	then mv -f ".deps/pcm_generic.Tpo" ".deps/pcm_generic.Plo"; else rm -f ".deps/pcm_generic.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_generic.lo -MD -MP -MF .deps/pcm_generic.Tpo -c pcm_generic.c  -fPIC -DPIC -o .libs/pcm_generic.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_plugin.lo -MD -MP -MF ".deps/pcm_plugin.Tpo" -c -o pcm_plugin.lo pcm_plugin.c; \
	then mv -f ".deps/pcm_plugin.Tpo" ".deps/pcm_plugin.Plo"; else rm -f ".deps/pcm_plugin.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_plugin.lo -MD -MP -MF .deps/pcm_plugin.Tpo -c pcm_plugin.c  -fPIC -DPIC -o .libs/pcm_plugin.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_copy.lo -MD -MP -MF ".deps/pcm_copy.Tpo" -c -o pcm_copy.lo pcm_copy.c; \
	then mv -f ".deps/pcm_copy.Tpo" ".deps/pcm_copy.Plo"; else rm -f ".deps/pcm_copy.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_copy.lo -MD -MP -MF .deps/pcm_copy.Tpo -c pcm_copy.c  -fPIC -DPIC -o .libs/pcm_copy.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_linear.lo -MD -MP -MF ".deps/pcm_linear.Tpo" -c -o pcm_linear.lo pcm_linear.c; \
	then mv -f ".deps/pcm_linear.Tpo" ".deps/pcm_linear.Plo"; else rm -f ".deps/pcm_linear.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_linear.lo -MD -MP -MF .deps/pcm_linear.Tpo -c pcm_linear.c  -fPIC -DPIC -o .libs/pcm_linear.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_route.lo -MD -MP -MF ".deps/pcm_route.Tpo" -c -o pcm_route.lo pcm_route.c; \
	then mv -f ".deps/pcm_route.Tpo" ".deps/pcm_route.Plo"; else rm -f ".deps/pcm_route.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_route.lo -MD -MP -MF .deps/pcm_route.Tpo -c pcm_route.c  -fPIC -DPIC -o .libs/pcm_route.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_mulaw.lo -MD -MP -MF ".deps/pcm_mulaw.Tpo" -c -o pcm_mulaw.lo pcm_mulaw.c; \
	then mv -f ".deps/pcm_mulaw.Tpo" ".deps/pcm_mulaw.Plo"; else rm -f ".deps/pcm_mulaw.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_mulaw.lo -MD -MP -MF .deps/pcm_mulaw.Tpo -c pcm_mulaw.c  -fPIC -DPIC -o .libs/pcm_mulaw.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_alaw.lo -MD -MP -MF ".deps/pcm_alaw.Tpo" -c -o pcm_alaw.lo pcm_alaw.c; \
	then mv -f ".deps/pcm_alaw.Tpo" ".deps/pcm_alaw.Plo"; else rm -f ".deps/pcm_alaw.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_alaw.lo -MD -MP -MF .deps/pcm_alaw.Tpo -c pcm_alaw.c  -fPIC -DPIC -o .libs/pcm_alaw.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_adpcm.lo -MD -MP -MF ".deps/pcm_adpcm.Tpo" -c -o pcm_adpcm.lo pcm_adpcm.c; \
	then mv -f ".deps/pcm_adpcm.Tpo" ".deps/pcm_adpcm.Plo"; else rm -f ".deps/pcm_adpcm.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_adpcm.lo -MD -MP -MF .deps/pcm_adpcm.Tpo -c pcm_adpcm.c  -fPIC -DPIC -o .libs/pcm_adpcm.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_rate.lo -MD -MP -MF ".deps/pcm_rate.Tpo" -c -o pcm_rate.lo pcm_rate.c; \
	then mv -f ".deps/pcm_rate.Tpo" ".deps/pcm_rate.Plo"; else rm -f ".deps/pcm_rate.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_rate.lo -MD -MP -MF .deps/pcm_rate.Tpo -c pcm_rate.c  -fPIC -DPIC -o .libs/pcm_rate.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_rate_linear.lo -MD -MP -MF ".deps/pcm_rate_linear.Tpo" -c -o pcm_rate_linear.lo pcm_rate_linear.c; \
	then mv -f ".deps/pcm_rate_linear.Tpo" ".deps/pcm_rate_linear.Plo"; else rm -f ".deps/pcm_rate_linear.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_rate_linear.lo -MD -MP -MF .deps/pcm_rate_linear.Tpo -c pcm_rate_linear.c  -fPIC -DPIC -o .libs/pcm_rate_linear.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_plug.lo -MD -MP -MF ".deps/pcm_plug.Tpo" -c -o pcm_plug.lo pcm_plug.c; \
	then mv -f ".deps/pcm_plug.Tpo" ".deps/pcm_plug.Plo"; else rm -f ".deps/pcm_plug.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_plug.lo -MD -MP -MF .deps/pcm_plug.Tpo -c pcm_plug.c  -fPIC -DPIC -o .libs/pcm_plug.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_multi.lo -MD -MP -MF ".deps/pcm_multi.Tpo" -c -o pcm_multi.lo pcm_multi.c; \
	then mv -f ".deps/pcm_multi.Tpo" ".deps/pcm_multi.Plo"; else rm -f ".deps/pcm_multi.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_multi.lo -MD -MP -MF .deps/pcm_multi.Tpo -c pcm_multi.c  -fPIC -DPIC -o .libs/pcm_multi.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_shm.lo -MD -MP -MF ".deps/pcm_shm.Tpo" -c -o pcm_shm.lo pcm_shm.c; \
	then mv -f ".deps/pcm_shm.Tpo" ".deps/pcm_shm.Plo"; else rm -f ".deps/pcm_shm.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_shm.lo -MD -MP -MF .deps/pcm_shm.Tpo -c pcm_shm.c  -fPIC -DPIC -o .libs/pcm_shm.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_file.lo -MD -MP -MF ".deps/pcm_file.Tpo" -c -o pcm_file.lo pcm_file.c; \
	then mv -f ".deps/pcm_file.Tpo" ".deps/pcm_file.Plo"; else rm -f ".deps/pcm_file.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_file.lo -MD -MP -MF .deps/pcm_file.Tpo -c pcm_file.c  -fPIC -DPIC -o .libs/pcm_file.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_null.lo -MD -MP -MF ".deps/pcm_null.Tpo" -c -o pcm_null.lo pcm_null.c; \
	then mv -f ".deps/pcm_null.Tpo" ".deps/pcm_null.Plo"; else rm -f ".deps/pcm_null.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_null.lo -MD -MP -MF .deps/pcm_null.Tpo -c pcm_null.c  -fPIC -DPIC -o .libs/pcm_null.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_empty.lo -MD -MP -MF ".deps/pcm_empty.Tpo" -c -o pcm_empty.lo pcm_empty.c; \
	then mv -f ".deps/pcm_empty.Tpo" ".deps/pcm_empty.Plo"; else rm -f ".deps/pcm_empty.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_empty.lo -MD -MP -MF .deps/pcm_empty.Tpo -c pcm_empty.c  -fPIC -DPIC -o .libs/pcm_empty.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_share.lo -MD -MP -MF ".deps/pcm_share.Tpo" -c -o pcm_share.lo pcm_share.c; \
	then mv -f ".deps/pcm_share.Tpo" ".deps/pcm_share.Plo"; else rm -f ".deps/pcm_share.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_share.lo -MD -MP -MF .deps/pcm_share.Tpo -c pcm_share.c  -fPIC -DPIC -o .libs/pcm_share.o
pcm_share.c: In function '_snd_pcm_share_missing':
pcm_share.c:295: warning: ignoring return value of 'read', declared with attribute warn_unused_result
pcm_share.c:297: warning: ignoring return value of 'write', declared with attribute warn_unused_result
pcm_share.c:300: warning: ignoring return value of 'write', declared with attribute warn_unused_result
pcm_share.c:302: warning: ignoring return value of 'read', declared with attribute warn_unused_result
pcm_share.c: In function 'snd_pcm_share_thread':
pcm_share.c:408: warning: ignoring return value of 'read', declared with attribute warn_unused_result
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_meter.lo -MD -MP -MF ".deps/pcm_meter.Tpo" -c -o pcm_meter.lo pcm_meter.c; \
	then mv -f ".deps/pcm_meter.Tpo" ".deps/pcm_meter.Plo"; else rm -f ".deps/pcm_meter.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_meter.lo -MD -MP -MF .deps/pcm_meter.Tpo -c pcm_meter.c  -fPIC -DPIC -o .libs/pcm_meter.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_hooks.lo -MD -MP -MF ".deps/pcm_hooks.Tpo" -c -o pcm_hooks.lo pcm_hooks.c; \
	then mv -f ".deps/pcm_hooks.Tpo" ".deps/pcm_hooks.Plo"; else rm -f ".deps/pcm_hooks.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_hooks.lo -MD -MP -MF .deps/pcm_hooks.Tpo -c pcm_hooks.c  -fPIC -DPIC -o .libs/pcm_hooks.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_lfloat.lo -MD -MP -MF ".deps/pcm_lfloat.Tpo" -c -o pcm_lfloat.lo pcm_lfloat.c; \
	then mv -f ".deps/pcm_lfloat.Tpo" ".deps/pcm_lfloat.Plo"; else rm -f ".deps/pcm_lfloat.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_lfloat.lo -MD -MP -MF .deps/pcm_lfloat.Tpo -c pcm_lfloat.c  -fPIC -DPIC -o .libs/pcm_lfloat.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_ladspa.lo -MD -MP -MF ".deps/pcm_ladspa.Tpo" -c -o pcm_ladspa.lo pcm_ladspa.c; \
	then mv -f ".deps/pcm_ladspa.Tpo" ".deps/pcm_ladspa.Plo"; else rm -f ".deps/pcm_ladspa.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_ladspa.lo -MD -MP -MF .deps/pcm_ladspa.Tpo -c pcm_ladspa.c  -fPIC -DPIC -o .libs/pcm_ladspa.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_dmix.lo -MD -MP -MF ".deps/pcm_dmix.Tpo" -c -o pcm_dmix.lo pcm_dmix.c; \
	then mv -f ".deps/pcm_dmix.Tpo" ".deps/pcm_dmix.Plo"; else rm -f ".deps/pcm_dmix.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_dmix.lo -MD -MP -MF .deps/pcm_dmix.Tpo -c pcm_dmix.c  -fPIC -DPIC -o .libs/pcm_dmix.o
In file included from pcm_dmix.c:144:
pcm_dmix_i386.c: In function 'mix_select_callbacks':
pcm_dmix_i386.c:102: warning: ignoring return value of 'fgets', declared with attribute warn_unused_result
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_dshare.lo -MD -MP -MF ".deps/pcm_dshare.Tpo" -c -o pcm_dshare.lo pcm_dshare.c; \
	then mv -f ".deps/pcm_dshare.Tpo" ".deps/pcm_dshare.Plo"; else rm -f ".deps/pcm_dshare.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_dshare.lo -MD -MP -MF .deps/pcm_dshare.Tpo -c pcm_dshare.c  -fPIC -DPIC -o .libs/pcm_dshare.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_dsnoop.lo -MD -MP -MF ".deps/pcm_dsnoop.Tpo" -c -o pcm_dsnoop.lo pcm_dsnoop.c; \
	then mv -f ".deps/pcm_dsnoop.Tpo" ".deps/pcm_dsnoop.Plo"; else rm -f ".deps/pcm_dsnoop.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_dsnoop.lo -MD -MP -MF .deps/pcm_dsnoop.Tpo -c pcm_dsnoop.c  -fPIC -DPIC -o .libs/pcm_dsnoop.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_direct.lo -MD -MP -MF ".deps/pcm_direct.Tpo" -c -o pcm_direct.lo pcm_direct.c; \
	then mv -f ".deps/pcm_direct.Tpo" ".deps/pcm_direct.Plo"; else rm -f ".deps/pcm_direct.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_direct.lo -MD -MP -MF .deps/pcm_direct.Tpo -c pcm_direct.c  -fPIC -DPIC -o .libs/pcm_direct.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_asym.lo -MD -MP -MF ".deps/pcm_asym.Tpo" -c -o pcm_asym.lo pcm_asym.c; \
	then mv -f ".deps/pcm_asym.Tpo" ".deps/pcm_asym.Plo"; else rm -f ".deps/pcm_asym.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_asym.lo -MD -MP -MF .deps/pcm_asym.Tpo -c pcm_asym.c  -fPIC -DPIC -o .libs/pcm_asym.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_iec958.lo -MD -MP -MF ".deps/pcm_iec958.Tpo" -c -o pcm_iec958.lo pcm_iec958.c; \
	then mv -f ".deps/pcm_iec958.Tpo" ".deps/pcm_iec958.Plo"; else rm -f ".deps/pcm_iec958.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_iec958.lo -MD -MP -MF .deps/pcm_iec958.Tpo -c pcm_iec958.c  -fPIC -DPIC -o .libs/pcm_iec958.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_softvol.lo -MD -MP -MF ".deps/pcm_softvol.Tpo" -c -o pcm_softvol.lo pcm_softvol.c; \
	then mv -f ".deps/pcm_softvol.Tpo" ".deps/pcm_softvol.Plo"; else rm -f ".deps/pcm_softvol.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_softvol.lo -MD -MP -MF .deps/pcm_softvol.Tpo -c pcm_softvol.c  -fPIC -DPIC -o .libs/pcm_softvol.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_extplug.lo -MD -MP -MF ".deps/pcm_extplug.Tpo" -c -o pcm_extplug.lo pcm_extplug.c; \
	then mv -f ".deps/pcm_extplug.Tpo" ".deps/pcm_extplug.Plo"; else rm -f ".deps/pcm_extplug.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_extplug.lo -MD -MP -MF .deps/pcm_extplug.Tpo -c pcm_extplug.c  -fPIC -DPIC -o .libs/pcm_extplug.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_ioplug.lo -MD -MP -MF ".deps/pcm_ioplug.Tpo" -c -o pcm_ioplug.lo pcm_ioplug.c; \
	then mv -f ".deps/pcm_ioplug.Tpo" ".deps/pcm_ioplug.Plo"; else rm -f ".deps/pcm_ioplug.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_ioplug.lo -MD -MP -MF .deps/pcm_ioplug.Tpo -c pcm_ioplug.c  -fPIC -DPIC -o .libs/pcm_ioplug.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_mmap_emul.lo -MD -MP -MF ".deps/pcm_mmap_emul.Tpo" -c -o pcm_mmap_emul.lo pcm_mmap_emul.c; \
	then mv -f ".deps/pcm_mmap_emul.Tpo" ".deps/pcm_mmap_emul.Plo"; else rm -f ".deps/pcm_mmap_emul.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_mmap_emul.lo -MD -MP -MF .deps/pcm_mmap_emul.Tpo -c pcm_mmap_emul.c  -fPIC -DPIC -o .libs/pcm_mmap_emul.o
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libpcm.la   atomic.lo mask.lo interval.lo pcm.lo pcm_params.lo pcm_simple.lo pcm_hw.lo pcm_misc.lo pcm_mmap.lo pcm_symbols.lo pcm_generic.lo pcm_plugin.lo pcm_copy.lo pcm_linear.lo pcm_route.lo pcm_mulaw.lo pcm_alaw.lo pcm_adpcm.lo pcm_rate.lo pcm_rate_linear.lo pcm_plug.lo pcm_multi.lo pcm_shm.lo pcm_file.lo pcm_null.lo pcm_empty.lo pcm_share.lo pcm_meter.lo pcm_hooks.lo pcm_lfloat.lo pcm_ladspa.lo pcm_dmix.lo pcm_dshare.lo pcm_dsnoop.lo pcm_direct.lo   pcm_asym.lo pcm_iec958.lo pcm_softvol.lo pcm_extplug.lo pcm_ioplug.lo pcm_mmap_emul.lo  
ar cru .libs/libpcm.a .libs/atomic.o .libs/mask.o .libs/interval.o .libs/pcm.o .libs/pcm_params.o .libs/pcm_simple.o .libs/pcm_hw.o .libs/pcm_misc.o .libs/pcm_mmap.o .libs/pcm_symbols.o .libs/pcm_generic.o .libs/pcm_plugin.o .libs/pcm_copy.o .libs/pcm_linear.o .libs/pcm_route.o .libs/pcm_mulaw.o .libs/pcm_alaw.o .libs/pcm_adpcm.o .libs/pcm_rate.o .libs/pcm_rate_linear.o .libs/pcm_plug.o .libs/pcm_multi.o .libs/pcm_shm.o .libs/pcm_file.o .libs/pcm_null.o .libs/pcm_empty.o .libs/pcm_share.o .libs/pcm_meter.o .libs/pcm_hooks.o .libs/pcm_lfloat.o .libs/pcm_ladspa.o .libs/pcm_dmix.o .libs/pcm_dshare.o .libs/pcm_dsnoop.o .libs/pcm_direct.o .libs/pcm_asym.o .libs/pcm_iec958.o .libs/pcm_softvol.o .libs/pcm_extplug.o .libs/pcm_ioplug.o .libs/pcm_mmap_emul.o
ranlib .libs/libpcm.a
creating libpcm.la
(cd .libs && rm -f libpcm.la && ln -s ../libpcm.la libpcm.la)
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/pcm'
Making all in timer
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/timer'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT timer.lo -MD -MP -MF ".deps/timer.Tpo" -c -o timer.lo timer.c; \
	then mv -f ".deps/timer.Tpo" ".deps/timer.Plo"; else rm -f ".deps/timer.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT timer.lo -MD -MP -MF .deps/timer.Tpo -c timer.c  -fPIC -DPIC -o .libs/timer.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT timer_hw.lo -MD -MP -MF ".deps/timer_hw.Tpo" -c -o timer_hw.lo timer_hw.c; \
	then mv -f ".deps/timer_hw.Tpo" ".deps/timer_hw.Plo"; else rm -f ".deps/timer_hw.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT timer_hw.lo -MD -MP -MF .deps/timer_hw.Tpo -c timer_hw.c  -fPIC -DPIC -o .libs/timer_hw.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT timer_query.lo -MD -MP -MF ".deps/timer_query.Tpo" -c -o timer_query.lo timer_query.c; \
	then mv -f ".deps/timer_query.Tpo" ".deps/timer_query.Plo"; else rm -f ".deps/timer_query.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT timer_query.lo -MD -MP -MF .deps/timer_query.Tpo -c timer_query.c  -fPIC -DPIC -o .libs/timer_query.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT timer_query_hw.lo -MD -MP -MF ".deps/timer_query_hw.Tpo" -c -o timer_query_hw.lo timer_query_hw.c; \
	then mv -f ".deps/timer_query_hw.Tpo" ".deps/timer_query_hw.Plo"; else rm -f ".deps/timer_query_hw.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT timer_query_hw.lo -MD -MP -MF .deps/timer_query_hw.Tpo -c timer_query_hw.c  -fPIC -DPIC -o .libs/timer_query_hw.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT timer_symbols.lo -MD -MP -MF ".deps/timer_symbols.Tpo" -c -o timer_symbols.lo timer_symbols.c; \
	then mv -f ".deps/timer_symbols.Tpo" ".deps/timer_symbols.Plo"; else rm -f ".deps/timer_symbols.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT timer_symbols.lo -MD -MP -MF .deps/timer_symbols.Tpo -c timer_symbols.c  -fPIC -DPIC -o .libs/timer_symbols.o
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libtimer.la   timer.lo timer_hw.lo timer_query.lo timer_query_hw.lo timer_symbols.lo  
ar cru .libs/libtimer.a .libs/timer.o .libs/timer_hw.o .libs/timer_query.o .libs/timer_query_hw.o .libs/timer_symbols.o
ranlib .libs/libtimer.a
creating libtimer.la
(cd .libs && rm -f libtimer.la && ln -s ../libtimer.la libtimer.la)
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/timer'
Making all in rawmidi
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/rawmidi'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT rawmidi.lo -MD -MP -MF ".deps/rawmidi.Tpo" -c -o rawmidi.lo rawmidi.c; \
	then mv -f ".deps/rawmidi.Tpo" ".deps/rawmidi.Plo"; else rm -f ".deps/rawmidi.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT rawmidi.lo -MD -MP -MF .deps/rawmidi.Tpo -c rawmidi.c  -fPIC -DPIC -o .libs/rawmidi.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT rawmidi_hw.lo -MD -MP -MF ".deps/rawmidi_hw.Tpo" -c -o rawmidi_hw.lo rawmidi_hw.c; \
	then mv -f ".deps/rawmidi_hw.Tpo" ".deps/rawmidi_hw.Plo"; else rm -f ".deps/rawmidi_hw.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT rawmidi_hw.lo -MD -MP -MF .deps/rawmidi_hw.Tpo -c rawmidi_hw.c  -fPIC -DPIC -o .libs/rawmidi_hw.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT rawmidi_symbols.lo -MD -MP -MF ".deps/rawmidi_symbols.Tpo" -c -o rawmidi_symbols.lo rawmidi_symbols.c; \
	then mv -f ".deps/rawmidi_symbols.Tpo" ".deps/rawmidi_symbols.Plo"; else rm -f ".deps/rawmidi_symbols.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT rawmidi_symbols.lo -MD -MP -MF .deps/rawmidi_symbols.Tpo -c rawmidi_symbols.c  -fPIC -DPIC -o .libs/rawmidi_symbols.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT rawmidi_virt.lo -MD -MP -MF ".deps/rawmidi_virt.Tpo" -c -o rawmidi_virt.lo rawmidi_virt.c; \
	then mv -f ".deps/rawmidi_virt.Tpo" ".deps/rawmidi_virt.Plo"; else rm -f ".deps/rawmidi_virt.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT rawmidi_virt.lo -MD -MP -MF .deps/rawmidi_virt.Tpo -c rawmidi_virt.c  -fPIC -DPIC -o .libs/rawmidi_virt.o
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2   -o librawmidi.la   rawmidi.lo rawmidi_hw.lo rawmidi_symbols.lo rawmidi_virt.lo  
ar cru .libs/librawmidi.a .libs/rawmidi.o .libs/rawmidi_hw.o .libs/rawmidi_symbols.o .libs/rawmidi_virt.o
ranlib .libs/librawmidi.a
creating librawmidi.la
(cd .libs && rm -f librawmidi.la && ln -s ../librawmidi.la librawmidi.la)
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/rawmidi'
Making all in hwdep
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/hwdep'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT hwdep.lo -MD -MP -MF ".deps/hwdep.Tpo" -c -o hwdep.lo hwdep.c; \
	then mv -f ".deps/hwdep.Tpo" ".deps/hwdep.Plo"; else rm -f ".deps/hwdep.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT hwdep.lo -MD -MP -MF .deps/hwdep.Tpo -c hwdep.c  -fPIC -DPIC -o .libs/hwdep.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT hwdep_hw.lo -MD -MP -MF ".deps/hwdep_hw.Tpo" -c -o hwdep_hw.lo hwdep_hw.c; \
	then mv -f ".deps/hwdep_hw.Tpo" ".deps/hwdep_hw.Plo"; else rm -f ".deps/hwdep_hw.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT hwdep_hw.lo -MD -MP -MF .deps/hwdep_hw.Tpo -c hwdep_hw.c  -fPIC -DPIC -o .libs/hwdep_hw.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT hwdep_symbols.lo -MD -MP -MF ".deps/hwdep_symbols.Tpo" -c -o hwdep_symbols.lo hwdep_symbols.c; \
	then mv -f ".deps/hwdep_symbols.Tpo" ".deps/hwdep_symbols.Plo"; else rm -f ".deps/hwdep_symbols.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT hwdep_symbols.lo -MD -MP -MF .deps/hwdep_symbols.Tpo -c hwdep_symbols.c  -fPIC -DPIC -o .libs/hwdep_symbols.o
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libhwdep.la   hwdep.lo hwdep_hw.lo hwdep_symbols.lo  
ar cru .libs/libhwdep.a .libs/hwdep.o .libs/hwdep_hw.o .libs/hwdep_symbols.o
ranlib .libs/libhwdep.a
creating libhwdep.la
(cd .libs && rm -f libhwdep.la && ln -s ../libhwdep.la libhwdep.la)
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/hwdep'
Making all in seq
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/seq'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_hw.lo -MD -MP -MF ".deps/seq_hw.Tpo" -c -o seq_hw.lo seq_hw.c; \
	then mv -f ".deps/seq_hw.Tpo" ".deps/seq_hw.Plo"; else rm -f ".deps/seq_hw.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_hw.lo -MD -MP -MF .deps/seq_hw.Tpo -c seq_hw.c  -fPIC -DPIC -o .libs/seq_hw.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq.lo -MD -MP -MF ".deps/seq.Tpo" -c -o seq.lo seq.c; \
	then mv -f ".deps/seq.Tpo" ".deps/seq.Plo"; else rm -f ".deps/seq.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq.lo -MD -MP -MF .deps/seq.Tpo -c seq.c  -fPIC -DPIC -o .libs/seq.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_event.lo -MD -MP -MF ".deps/seq_event.Tpo" -c -o seq_event.lo seq_event.c; \
	then mv -f ".deps/seq_event.Tpo" ".deps/seq_event.Plo"; else rm -f ".deps/seq_event.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_event.lo -MD -MP -MF .deps/seq_event.Tpo -c seq_event.c  -fPIC -DPIC -o .libs/seq_event.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seqmid.lo -MD -MP -MF ".deps/seqmid.Tpo" -c -o seqmid.lo seqmid.c; \
	then mv -f ".deps/seqmid.Tpo" ".deps/seqmid.Plo"; else rm -f ".deps/seqmid.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seqmid.lo -MD -MP -MF .deps/seqmid.Tpo -c seqmid.c  -fPIC -DPIC -o .libs/seqmid.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_midi_event.lo -MD -MP -MF ".deps/seq_midi_event.Tpo" -c -o seq_midi_event.lo seq_midi_event.c; \
	then mv -f ".deps/seq_midi_event.Tpo" ".deps/seq_midi_event.Plo"; else rm -f ".deps/seq_midi_event.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_midi_event.lo -MD -MP -MF .deps/seq_midi_event.Tpo -c seq_midi_event.c  -fPIC -DPIC -o .libs/seq_midi_event.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_symbols.lo -MD -MP -MF ".deps/seq_symbols.Tpo" -c -o seq_symbols.lo seq_symbols.c; \
	then mv -f ".deps/seq_symbols.Tpo" ".deps/seq_symbols.Plo"; else rm -f ".deps/seq_symbols.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_symbols.lo -MD -MP -MF .deps/seq_symbols.Tpo -c seq_symbols.c  -fPIC -DPIC -o .libs/seq_symbols.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_old.lo -MD -MP -MF ".deps/seq_old.Tpo" -c -o seq_old.lo seq_old.c; \
	then mv -f ".deps/seq_old.Tpo" ".deps/seq_old.Plo"; else rm -f ".deps/seq_old.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_old.lo -MD -MP -MF .deps/seq_old.Tpo -c seq_old.c  -fPIC -DPIC -o .libs/seq_old.o
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libseq.la   seq_hw.lo seq.lo seq_event.lo seqmid.lo seq_midi_event.lo seq_symbols.lo seq_old.lo  
ar cru .libs/libseq.a .libs/seq_hw.o .libs/seq.o .libs/seq_event.o .libs/seqmid.o .libs/seq_midi_event.o .libs/seq_symbols.o .libs/seq_old.o
ranlib .libs/libseq.a
creating libseq.la
(cd .libs && rm -f libseq.la && ln -s ../libseq.la libseq.la)
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/seq'
Making all in alisp
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/alisp'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT alisp.lo -MD -MP -MF ".deps/alisp.Tpo" -c -o alisp.lo alisp.c; \
	then mv -f ".deps/alisp.Tpo" ".deps/alisp.Plo"; else rm -f ".deps/alisp.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT alisp.lo -MD -MP -MF .deps/alisp.Tpo -c alisp.c  -fPIC -DPIC -o .libs/alisp.o
alisp.c: In function 'F_princ':
alisp.c:1711: warning: format not a string literal and no format arguments
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libalisp.la   alisp.lo  
ar cru .libs/libalisp.a .libs/alisp.o
ranlib .libs/libalisp.a
creating libalisp.la
(cd .libs && rm -f libalisp.la && ln -s ../libalisp.la libalisp.la)
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/alisp'
Making all in compat
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/compat'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include     -g -O2 -MT empty.lo -MD -MP -MF ".deps/empty.Tpo" -c -o empty.lo empty.c; \
	then mv -f ".deps/empty.Tpo" ".deps/empty.Plo"; else rm -f ".deps/empty.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -g -O2 -MT empty.lo -MD -MP -MF .deps/empty.Tpo -c empty.c  -fPIC -DPIC -o .libs/empty.o
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libcompat.la   empty.lo  
ar cru .libs/libcompat.a .libs/empty.o
ranlib .libs/libcompat.a
creating libcompat.la
(cd .libs && rm -f libcompat.la && ln -s ../libcompat.la libcompat.la)
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/compat'
Making all in conf
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf'
Making all in cards
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/cards'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/cards'
Making all in pcm
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/pcm'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/pcm'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf'
make[3]: Für das Ziel »all-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT conf.lo -MD -MP -MF ".deps/conf.Tpo" -c -o conf.lo conf.c; \
	then mv -f ".deps/conf.Tpo" ".deps/conf.Plo"; else rm -f ".deps/conf.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT conf.lo -MD -MP -MF .deps/conf.Tpo -c conf.c  -fPIC -DPIC -o .libs/conf.o
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT confmisc.lo -MD -MP -MF ".deps/confmisc.Tpo" -c -o confmisc.lo confmisc.c; \
	then mv -f ".deps/confmisc.Tpo" ".deps/confmisc.Plo"; else rm -f ".deps/confmisc.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT confmisc.lo -MD -MP -MF .deps/confmisc.Tpo -c confmisc.c  -fPIC -DPIC -o .libs/confmisc.o
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT input.lo -MD -MP -MF ".deps/input.Tpo" -c -o input.lo input.c; \
	then mv -f ".deps/input.Tpo" ".deps/input.Plo"; else rm -f ".deps/input.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT input.lo -MD -MP -MF .deps/input.Tpo -c input.c  -fPIC -DPIC -o .libs/input.o
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT output.lo -MD -MP -MF ".deps/output.Tpo" -c -o output.lo output.c; \
	then mv -f ".deps/output.Tpo" ".deps/output.Plo"; else rm -f ".deps/output.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT output.lo -MD -MP -MF .deps/output.Tpo -c output.c  -fPIC -DPIC -o .libs/output.o
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT async.lo -MD -MP -MF ".deps/async.Tpo" -c -o async.lo async.c; \
	then mv -f ".deps/async.Tpo" ".deps/async.Plo"; else rm -f ".deps/async.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT async.lo -MD -MP -MF .deps/async.Tpo -c async.c  -fPIC -DPIC -o .libs/async.o
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT error.lo -MD -MP -MF ".deps/error.Tpo" -c -o error.lo error.c; \
	then mv -f ".deps/error.Tpo" ".deps/error.Plo"; else rm -f ".deps/error.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT error.lo -MD -MP -MF .deps/error.Tpo -c error.c  -fPIC -DPIC -o .libs/error.o
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT dlmisc.lo -MD -MP -MF ".deps/dlmisc.Tpo" -c -o dlmisc.lo dlmisc.c; \
	then mv -f ".deps/dlmisc.Tpo" ".deps/dlmisc.Plo"; else rm -f ".deps/dlmisc.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT dlmisc.lo -MD -MP -MF .deps/dlmisc.Tpo -c dlmisc.c  -fPIC -DPIC -o .libs/dlmisc.o
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT socket.lo -MD -MP -MF ".deps/socket.Tpo" -c -o socket.lo socket.c; \
	then mv -f ".deps/socket.Tpo" ".deps/socket.Plo"; else rm -f ".deps/socket.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT socket.lo -MD -MP -MF .deps/socket.Tpo -c socket.c  -fPIC -DPIC -o .libs/socket.o
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT shmarea.lo -MD -MP -MF ".deps/shmarea.Tpo" -c -o shmarea.lo shmarea.c; \
	then mv -f ".deps/shmarea.Tpo" ".deps/shmarea.Plo"; else rm -f ".deps/shmarea.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT shmarea.lo -MD -MP -MF .deps/shmarea.Tpo -c shmarea.c  -fPIC -DPIC -o .libs/shmarea.o
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT userfile.lo -MD -MP -MF ".deps/userfile.Tpo" -c -o userfile.lo userfile.c; \
	then mv -f ".deps/userfile.Tpo" ".deps/userfile.Plo"; else rm -f ".deps/userfile.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT userfile.lo -MD -MP -MF .deps/userfile.Tpo -c userfile.c  -fPIC -DPIC -o .libs/userfile.o
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT names.lo -MD -MP -MF ".deps/names.Tpo" -c -o names.lo names.c; \
	then mv -f ".deps/names.Tpo" ".deps/names.Plo"; else rm -f ".deps/names.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT names.lo -MD -MP -MF .deps/names.Tpo -c names.c  -fPIC -DPIC -o .libs/names.o
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o libasound.la -rpath /usr/lib -version-info 2:0:0 -Wl,--version-script=Versions  conf.lo confmisc.lo input.lo output.lo async.lo error.lo dlmisc.lo socket.lo shmarea.lo userfile.lo names.lo control/libcontrol.la mixer/libmixer.la pcm/libpcm.la timer/libtimer.la rawmidi/librawmidi.la hwdep/libhwdep.la seq/libseq.la alisp/libalisp.la compat/libcompat.la -lm -ldl -lpthread -lrt  
gcc -shared  .libs/conf.o .libs/confmisc.o .libs/input.o .libs/output.o .libs/async.o .libs/error.o .libs/dlmisc.o .libs/socket.o .libs/shmarea.o .libs/userfile.o .libs/names.o -Wl,--whole-archive control/.libs/libcontrol.a mixer/.libs/libmixer.a pcm/.libs/libpcm.a timer/.libs/libtimer.a rawmidi/.libs/librawmidi.a hwdep/.libs/libhwdep.a seq/.libs/libseq.a alisp/.libs/libalisp.a compat/.libs/libcompat.a -Wl,--no-whole-archive  -lm -ldl -lpthread -lrt  -Wl,--version-script=Versions -Wl,-soname -Wl,libasound.so.2 -o .libs/libasound.so.2.0.0
(cd .libs && rm -f libasound.so.2 && ln -s libasound.so.2.0.0 libasound.so.2)
(cd .libs && rm -f libasound.so && ln -s libasound.so.2.0.0 libasound.so)
creating libasound.la
(cd .libs && rm -f libasound.la && ln -s ../libasound.la libasound.la)
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src'
Making all in modules
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules'
Making all in mixer
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer'
Making all in simple
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer/simple'
if /bin/bash ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include   -g -O2 -W -Wall -g -O2 -MT sbase.lo -MD -MP -MF ".deps/sbase.Tpo" -c -o sbase.lo sbase.c; \
	then mv -f ".deps/sbase.Tpo" ".deps/sbase.Plo"; else rm -f ".deps/sbase.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include -g -O2 -W -Wall -g -O2 -MT sbase.lo -MD -MP -MF .deps/sbase.Tpo -c sbase.c  -fPIC -DPIC -o .libs/sbase.o
/bin/bash ../../../libtool --tag=CC --mode=link gcc -g -O2 -W -Wall -g -O2   -o smixer-sbase.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version sbase.lo ../../../src/libasound.la 
gcc -shared  .libs/sbase.o  -Wl,--rpath -Wl,/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/.libs ../../../src/.libs/libasound.so  -Wl,-soname -Wl,smixer-sbase.so -o .libs/smixer-sbase.so
creating smixer-sbase.la
(cd .libs && rm -f smixer-sbase.la && ln -s ../smixer-sbase.la smixer-sbase.la)
if /bin/bash ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include   -g -O2 -W -Wall -g -O2 -MT ac97.lo -MD -MP -MF ".deps/ac97.Tpo" -c -o ac97.lo ac97.c; \
	then mv -f ".deps/ac97.Tpo" ".deps/ac97.Plo"; else rm -f ".deps/ac97.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include -g -O2 -W -Wall -g -O2 -MT ac97.lo -MD -MP -MF .deps/ac97.Tpo -c ac97.c  -fPIC -DPIC -o .libs/ac97.o
if /bin/bash ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include   -g -O2 -W -Wall -g -O2 -MT sbasedl.lo -MD -MP -MF ".deps/sbasedl.Tpo" -c -o sbasedl.lo sbasedl.c; \
	then mv -f ".deps/sbasedl.Tpo" ".deps/sbasedl.Plo"; else rm -f ".deps/sbasedl.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include -g -O2 -W -Wall -g -O2 -MT sbasedl.lo -MD -MP -MF .deps/sbasedl.Tpo -c sbasedl.c  -fPIC -DPIC -o .libs/sbasedl.o
/bin/bash ../../../libtool --tag=CC --mode=link gcc -g -O2 -W -Wall -g -O2   -o smixer-ac97.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version ac97.lo sbasedl.lo ../../../src/libasound.la 
gcc -shared  .libs/ac97.o .libs/sbasedl.o  -Wl,--rpath -Wl,/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/.libs ../../../src/.libs/libasound.so  -Wl,-soname -Wl,smixer-ac97.so -o .libs/smixer-ac97.so
creating smixer-ac97.la
(cd .libs && rm -f smixer-ac97.la && ln -s ../smixer-ac97.la smixer-ac97.la)
if /bin/bash ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include   -g -O2 -W -Wall -g -O2 -MT hda.lo -MD -MP -MF ".deps/hda.Tpo" -c -o hda.lo hda.c; \
	then mv -f ".deps/hda.Tpo" ".deps/hda.Plo"; else rm -f ".deps/hda.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include -g -O2 -W -Wall -g -O2 -MT hda.lo -MD -MP -MF .deps/hda.Tpo -c hda.c  -fPIC -DPIC -o .libs/hda.o
/bin/bash ../../../libtool --tag=CC --mode=link gcc -g -O2 -W -Wall -g -O2   -o smixer-hda.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version hda.lo sbasedl.lo ../../../src/libasound.la 
gcc -shared  .libs/hda.o .libs/sbasedl.o  -Wl,--rpath -Wl,/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/.libs ../../../src/.libs/libasound.so  -Wl,-soname -Wl,smixer-hda.so -o .libs/smixer-hda.so
creating smixer-hda.la
(cd .libs && rm -f smixer-hda.la && ln -s ../smixer-hda.la smixer-hda.la)
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer/simple'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer'
make[3]: Für das Ziel »all-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules'
make[2]: Für das Ziel »all-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules'
Making all in aserver
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/aserver'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../src/pcm    -g -O2 -MT aserver.o -MD -MP -MF ".deps/aserver.Tpo" -c -o aserver.o aserver.c; \
	then mv -f ".deps/aserver.Tpo" ".deps/aserver.Po"; else rm -f ".deps/aserver.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o aserver  aserver.o ../src/libasound.la 
mkdir .libs
gcc -g -O2 -o .libs/aserver aserver.o  ../src/.libs/libasound.so -lm -ldl -lpthread -lrt
creating aserver
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/aserver'
Making all in alsalisp
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/alsalisp'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../src/alisp    -g -O2 -MT alsalisp.o -MD -MP -MF ".deps/alsalisp.Tpo" -c -o alsalisp.o alsalisp.c; \
	then mv -f ".deps/alsalisp.Tpo" ".deps/alsalisp.Po"; else rm -f ".deps/alsalisp.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o alsalisp  alsalisp.o ../src/libasound.la 
mkdir .libs
gcc -g -O2 -o .libs/alsalisp alsalisp.o  ../src/.libs/libasound.so -lm -ldl -lpthread -lrt
creating alsalisp
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/alsalisp'
Making all in test
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/test'
make[1]: Für das Ziel »all« ist nichts zu tun.
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/test'
Making all in utils
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/utils'
make[1]: Für das Ziel »all« ist nichts zu tun.
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/utils'
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16'
make[1]: Für das Ziel »all-am« ist nichts zu tun.
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16'
Making install in doc
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc'
Making install in pictures
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc/pictures'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc/pictures'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc/pictures'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc/pictures'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/doc'
Making install in include
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
Making install in sound
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include/sound'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include/sound'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
test -z "/usr/include/alsa/sound" || mkdir -p -- "/usr/include/alsa/sound"
 /usr/bin/install -c -m 644 'asound_fm.h' '/usr/include/alsa/sound/asound_fm.h'
 /usr/bin/install -c -m 644 'hdsp.h' '/usr/include/alsa/sound/hdsp.h'
 /usr/bin/install -c -m 644 'sb16_csp.h' '/usr/include/alsa/sound/sb16_csp.h'
 /usr/bin/install -c -m 644 'sscape_ioctl.h' '/usr/include/alsa/sound/sscape_ioctl.h'
 /usr/bin/install -c -m 644 'emu10k1.h' '/usr/include/alsa/sound/emu10k1.h'
 /usr/bin/install -c -m 644 'type_compat.h' '/usr/include/alsa/sound/type_compat.h'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include/sound'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include/sound'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
test -z "/usr/include/alsa" || mkdir -p -- "/usr/include/alsa"
 /usr/bin/install -c -m 644 'asoundlib.h' '/usr/include/alsa/asoundlib.h'
 /usr/bin/install -c -m 644 'asoundef.h' '/usr/include/alsa/asoundef.h'
 /usr/bin/install -c -m 644 'version.h' '/usr/include/alsa/version.h'
 /usr/bin/install -c -m 644 'global.h' '/usr/include/alsa/global.h'
 /usr/bin/install -c -m 644 'input.h' '/usr/include/alsa/input.h'
 /usr/bin/install -c -m 644 'output.h' '/usr/include/alsa/output.h'
 /usr/bin/install -c -m 644 'error.h' '/usr/include/alsa/error.h'
 /usr/bin/install -c -m 644 'conf.h' '/usr/include/alsa/conf.h'
 /usr/bin/install -c -m 644 'control.h' '/usr/include/alsa/control.h'
 /usr/bin/install -c -m 644 'iatomic.h' '/usr/include/alsa/iatomic.h'
 /usr/bin/install -c -m 644 'control_external.h' '/usr/include/alsa/control_external.h'
 /usr/bin/install -c -m 644 'pcm.h' '/usr/include/alsa/pcm.h'
 /usr/bin/install -c -m 644 'pcm_old.h' '/usr/include/alsa/pcm_old.h'
 /usr/bin/install -c -m 644 'timer.h' '/usr/include/alsa/timer.h'
 /usr/bin/install -c -m 644 'pcm_plugin.h' '/usr/include/alsa/pcm_plugin.h'
 /usr/bin/install -c -m 644 'pcm_rate.h' '/usr/include/alsa/pcm_rate.h'
 /usr/bin/install -c -m 644 'pcm_external.h' '/usr/include/alsa/pcm_external.h'
 /usr/bin/install -c -m 644 'pcm_extplug.h' '/usr/include/alsa/pcm_extplug.h'
 /usr/bin/install -c -m 644 'pcm_ioplug.h' '/usr/include/alsa/pcm_ioplug.h'
 /usr/bin/install -c -m 644 'rawmidi.h' '/usr/include/alsa/rawmidi.h'
 /usr/bin/install -c -m 644 'hwdep.h' '/usr/include/alsa/hwdep.h'
 /usr/bin/install -c -m 644 'mixer.h' '/usr/include/alsa/mixer.h'
 /usr/bin/install -c -m 644 'mixer_abst.h' '/usr/include/alsa/mixer_abst.h'
 /usr/bin/install -c -m 644 'seq_event.h' '/usr/include/alsa/seq_event.h'
 /usr/bin/install -c -m 644 'seq.h' '/usr/include/alsa/seq.h'
 /usr/bin/install -c -m 644 'seqmid.h' '/usr/include/alsa/seqmid.h'
 /usr/bin/install -c -m 644 'seq_midi_event.h' '/usr/include/alsa/seq_midi_event.h'
 /usr/bin/install -c -m 644 'alisp.h' '/usr/include/alsa/alisp.h'
make  install-data-hook
make[4]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
test -d /usr/include/sys || mkdir -p /usr/include/sys
/usr/bin/install -c -m 644 ./sys.h /usr/include/sys/asoundlib.h
make[4]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/include'
Making install in src
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src'
Making install in control
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/control'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/control'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/control'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/control'
Making install in mixer
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/mixer'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/mixer'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/mixer'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/mixer'
Making install in pcm
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/pcm'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/pcm'
make[4]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/pcm'
make[4]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[4]: Für das Ziel »install-data-am« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/pcm'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/pcm'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/pcm'
Making install in timer
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/timer'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/timer'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/timer'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/timer'
Making install in rawmidi
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/rawmidi'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/rawmidi'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/rawmidi'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/rawmidi'
Making install in hwdep
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/hwdep'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/hwdep'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/hwdep'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/hwdep'
Making install in seq
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/seq'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/seq'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/seq'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/seq'
Making install in alisp
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/alisp'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/alisp'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/alisp'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/alisp'
Making install in compat
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/compat'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/compat'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/compat'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/compat'
Making install in conf
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf'
Making install in cards
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/cards'
make[4]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/cards'
make[4]: Für das Ziel »install-exec-am« ist nichts zu tun.
test -z "/usr/share/alsa/cards/SI7018" || mkdir -p -- "/usr/share/alsa/cards/SI7018"
 /usr/bin/install -c -m 644 'SI7018/sndoc-mixer.alisp' '/usr/share/alsa/cards/SI7018/sndoc-mixer.alisp'
 /usr/bin/install -c -m 644 'SI7018/sndop-mixer.alisp' '/usr/share/alsa/cards/SI7018/sndop-mixer.alisp'
test -z "/usr/share/alsa/cards" || mkdir -p -- "/usr/share/alsa/cards"
 /usr/bin/install -c -m 644 'aliases.conf' '/usr/share/alsa/cards/aliases.conf'
 /usr/bin/install -c -m 644 'AACI.conf' '/usr/share/alsa/cards/AACI.conf'
 /usr/bin/install -c -m 644 'ATIIXP.conf' '/usr/share/alsa/cards/ATIIXP.conf'
 /usr/bin/install -c -m 644 'ATIIXP-SPDMA.conf' '/usr/share/alsa/cards/ATIIXP-SPDMA.conf'
 /usr/bin/install -c -m 644 'ATIIXP-MODEM.conf' '/usr/share/alsa/cards/ATIIXP-MODEM.conf'
 /usr/bin/install -c -m 644 'AU8810.conf' '/usr/share/alsa/cards/AU8810.conf'
 /usr/bin/install -c -m 644 'AU8820.conf' '/usr/share/alsa/cards/AU8820.conf'
 /usr/bin/install -c -m 644 'AU8830.conf' '/usr/share/alsa/cards/AU8830.conf'
 /usr/bin/install -c -m 644 'Audigy.conf' '/usr/share/alsa/cards/Audigy.conf'
 /usr/bin/install -c -m 644 'Audigy2.conf' '/usr/share/alsa/cards/Audigy2.conf'
 /usr/bin/install -c -m 644 'Aureon51.conf' '/usr/share/alsa/cards/Aureon51.conf'
 /usr/bin/install -c -m 644 'Aureon71.conf' '/usr/share/alsa/cards/Aureon71.conf'
 /usr/bin/install -c -m 644 'CA0106.conf' '/usr/share/alsa/cards/CA0106.conf'
 /usr/bin/install -c -m 644 'CMI8338.conf' '/usr/share/alsa/cards/CMI8338.conf'
 /usr/bin/install -c -m 644 'CMI8338-SWIEC.conf' '/usr/share/alsa/cards/CMI8338-SWIEC.conf'
 /usr/bin/install -c -m 644 'CMI8738-MC6.conf' '/usr/share/alsa/cards/CMI8738-MC6.conf'
 /usr/bin/install -c -m 644 'CMI8738-MC8.conf' '/usr/share/alsa/cards/CMI8738-MC8.conf'
 /usr/bin/install -c -m 644 'CMI8788.conf' '/usr/share/alsa/cards/CMI8788.conf'
 /usr/bin/install -c -m 644 'CS46xx.conf' '/usr/share/alsa/cards/CS46xx.conf'
 /usr/bin/install -c -m 644 'EMU10K1.conf' '/usr/share/alsa/cards/EMU10K1.conf'
 /usr/bin/install -c -m 644 'EMU10K1X.conf' '/usr/share/alsa/cards/EMU10K1X.conf'
 /usr/bin/install -c -m 644 'ENS1370.conf' '/usr/share/alsa/cards/ENS1370.conf'
 /usr/bin/install -c -m 644 'ENS1371.conf' '/usr/share/alsa/cards/ENS1371.conf'
 /usr/bin/install -c -m 644 'ES1968.conf' '/usr/share/alsa/cards/ES1968.conf'
 /usr/bin/install -c -m 644 'FM801.conf' '/usr/share/alsa/cards/FM801.conf'
 /usr/bin/install -c -m 644 'GUS.conf' '/usr/share/alsa/cards/GUS.conf'
 /usr/bin/install -c -m 644 'HDA-Intel.conf' '/usr/share/alsa/cards/HDA-Intel.conf'
 /usr/bin/install -c -m 644 'ICE1712.conf' '/usr/share/alsa/cards/ICE1712.conf'
 /usr/bin/install -c -m 644 'ICE1724.conf' '/usr/share/alsa/cards/ICE1724.conf'
 /usr/bin/install -c -m 644 'ICH.conf' '/usr/share/alsa/cards/ICH.conf'
 /usr/bin/install -c -m 644 'ICH4.conf' '/usr/share/alsa/cards/ICH4.conf'
 /usr/bin/install -c -m 644 'ICH-MODEM.conf' '/usr/share/alsa/cards/ICH-MODEM.conf'
 /usr/bin/install -c -m 644 'Maestro3.conf' '/usr/share/alsa/cards/Maestro3.conf'
 /usr/bin/install -c -m 644 'NFORCE.conf' '/usr/share/alsa/cards/NFORCE.conf'
 /usr/bin/install -c -m 644 'PC-Speaker.conf' '/usr/share/alsa/cards/PC-Speaker.conf'
 /usr/bin/install -c -m 644 'PMac.conf' '/usr/share/alsa/cards/PMac.conf'
 /usr/bin/install -c -m 644 'PMacToonie.conf' '/usr/share/alsa/cards/PMacToonie.conf'
 /usr/bin/install -c -m 644 'PS3.conf' '/usr/share/alsa/cards/PS3.conf'
 /usr/bin/install -c -m 644 'RME9636.conf' '/usr/share/alsa/cards/RME9636.conf'
 /usr/bin/install -c -m 644 'RME9652.conf' '/usr/share/alsa/cards/RME9652.conf'
 /usr/bin/install -c -m 644 'SI7018.conf' '/usr/share/alsa/cards/SI7018.conf'
 /usr/bin/install -c -m 644 'TRID4DWAVENX.conf' '/usr/share/alsa/cards/TRID4DWAVENX.conf'
 /usr/bin/install -c -m 644 'USB-Audio.conf' '/usr/share/alsa/cards/USB-Audio.conf'
 /usr/bin/install -c -m 644 'YMF744.conf' '/usr/share/alsa/cards/YMF744.conf'
 /usr/bin/install -c -m 644 'VIA686A.conf' '/usr/share/alsa/cards/VIA686A.conf'
 /usr/bin/install -c -m 644 'VIA8233.conf' '/usr/share/alsa/cards/VIA8233.conf'
 /usr/bin/install -c -m 644 'VIA8233A.conf' '/usr/share/alsa/cards/VIA8233A.conf'
 /usr/bin/install -c -m 644 'VIA8237.conf' '/usr/share/alsa/cards/VIA8237.conf'
 /usr/bin/install -c -m 644 'VX222.conf' '/usr/share/alsa/cards/VX222.conf'
 /usr/bin/install -c -m 644 'VXPocket.conf' '/usr/share/alsa/cards/VXPocket.conf'
 /usr/bin/install -c -m 644 'VXPocket440.conf' '/usr/share/alsa/cards/VXPocket440.conf'
 /usr/bin/install -c -m 644 'aliases.alisp' '/usr/share/alsa/cards/aliases.alisp'
make[4]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/cards'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/cards'
Making install in pcm
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/pcm'
make[4]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/pcm'
make[4]: Für das Ziel »install-exec-am« ist nichts zu tun.
test -z "/usr/share/alsa/pcm" || mkdir -p -- "/usr/share/alsa/pcm"
 /usr/bin/install -c -m 644 'default.conf' '/usr/share/alsa/pcm/default.conf'
 /usr/bin/install -c -m 644 'front.conf' '/usr/share/alsa/pcm/front.conf'
 /usr/bin/install -c -m 644 'rear.conf' '/usr/share/alsa/pcm/rear.conf'
 /usr/bin/install -c -m 644 'center_lfe.conf' '/usr/share/alsa/pcm/center_lfe.conf'
 /usr/bin/install -c -m 644 'side.conf' '/usr/share/alsa/pcm/side.conf'
 /usr/bin/install -c -m 644 'surround40.conf' '/usr/share/alsa/pcm/surround40.conf'
 /usr/bin/install -c -m 644 'surround41.conf' '/usr/share/alsa/pcm/surround41.conf'
 /usr/bin/install -c -m 644 'surround50.conf' '/usr/share/alsa/pcm/surround50.conf'
 /usr/bin/install -c -m 644 'surround51.conf' '/usr/share/alsa/pcm/surround51.conf'
 /usr/bin/install -c -m 644 'surround71.conf' '/usr/share/alsa/pcm/surround71.conf'
 /usr/bin/install -c -m 644 'iec958.conf' '/usr/share/alsa/pcm/iec958.conf'
 /usr/bin/install -c -m 644 'modem.conf' '/usr/share/alsa/pcm/modem.conf'
 /usr/bin/install -c -m 644 'dmix.conf' '/usr/share/alsa/pcm/dmix.conf'
 /usr/bin/install -c -m 644 'dsnoop.conf' '/usr/share/alsa/pcm/dsnoop.conf'
 /usr/bin/install -c -m 644 'dpl.conf' '/usr/share/alsa/pcm/dpl.conf'
make[4]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/pcm'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf/pcm'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf'
make[4]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf'
make[4]: Für das Ziel »install-exec-am« ist nichts zu tun.
test -z "/usr/share/alsa" || mkdir -p -- "/usr/share/alsa"
 /usr/bin/install -c -m 644 'alsa.conf' '/usr/share/alsa/alsa.conf'
 /usr/bin/install -c -m 644 'sndo-mixer.alisp' '/usr/share/alsa/sndo-mixer.alisp'
 /usr/bin/install -c -m 644 'smixer.conf' '/usr/share/alsa/smixer.conf'
make[4]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src/conf'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libasound.la' '/usr/lib/libasound.la'
/usr/bin/install -c .libs/libasound.so.2.0.0 /usr/lib/libasound.so.2.0.0
(cd /usr/lib && { ln -s -f libasound.so.2.0.0 libasound.so.2 || { rm -f libasound.so.2 && ln -s libasound.so.2.0.0 libasound.so.2; }; })
(cd /usr/lib && { ln -s -f libasound.so.2.0.0 libasound.so || { rm -f libasound.so && ln -s libasound.so.2.0.0 libasound.so; }; })
/usr/bin/install -c .libs/libasound.lai /usr/lib/libasound.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/src'
Making install in modules
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules'
Making install in mixer
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer'
Making install in simple
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer/simple'
make[4]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer/simple'
test -z "/usr/lib/alsa-lib/smixer" || mkdir -p -- "/usr/lib/alsa-lib/smixer"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'smixer-sbase.la' '/usr/lib/alsa-lib/smixer/smixer-sbase.la'
libtool: install: warning: relinking `smixer-sbase.la'
(cd /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer/simple; /bin/bash ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-sbase.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version sbase.lo ../../../src/libasound.la )
gcc -shared  .libs/sbase.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-sbase.so -o .libs/smixer-sbase.so
/usr/bin/install -c .libs/smixer-sbase.soT /usr/lib/alsa-lib/smixer/smixer-sbase.so
/usr/bin/install -c .libs/smixer-sbase.lai /usr/lib/alsa-lib/smixer/smixer-sbase.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/alsa-lib/smixer

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'smixer-ac97.la' '/usr/lib/alsa-lib/smixer/smixer-ac97.la'
libtool: install: warning: relinking `smixer-ac97.la'
(cd /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer/simple; /bin/bash ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-ac97.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version ac97.lo sbasedl.lo ../../../src/libasound.la )
gcc -shared  .libs/ac97.o .libs/sbasedl.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-ac97.so -o .libs/smixer-ac97.so
/usr/bin/install -c .libs/smixer-ac97.soT /usr/lib/alsa-lib/smixer/smixer-ac97.so
/usr/bin/install -c .libs/smixer-ac97.lai /usr/lib/alsa-lib/smixer/smixer-ac97.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/alsa-lib/smixer

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'smixer-hda.la' '/usr/lib/alsa-lib/smixer/smixer-hda.la'
libtool: install: warning: relinking `smixer-hda.la'
(cd /home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer/simple; /bin/bash ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-hda.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version hda.lo sbasedl.lo ../../../src/libasound.la )
gcc -shared  .libs/hda.o .libs/sbasedl.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-hda.so -o .libs/smixer-hda.so
/usr/bin/install -c .libs/smixer-hda.soT /usr/lib/alsa-lib/smixer/smixer-hda.so
/usr/bin/install -c .libs/smixer-hda.lai /usr/lib/alsa-lib/smixer/smixer-hda.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/alsa-lib/smixer

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Für das Ziel »install-data-am« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer/simple'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer/simple'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer'
make[4]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer'
make[4]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[4]: Für das Ziel »install-data-am« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer'
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules/mixer'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules'
make[3]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/modules'
Making install in aserver
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/aserver'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/aserver'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'aserver' '/usr/bin/aserver'
/usr/bin/install -c .libs/aserver /usr/bin/aserver
make[2]: Für das Ziel »install-data-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/aserver'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/aserver'
Making install in alsalisp
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/alsalisp'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/alsalisp'
make[2]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[2]: Für das Ziel »install-data-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/alsalisp'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/alsalisp'
Making install in test
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/test'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/test'
make[2]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[2]: Für das Ziel »install-data-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/test'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/test'
Making install in utils
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/utils'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/utils'
make[2]: Für das Ziel »install-exec-am« ist nichts zu tun.
test -z "/usr/share/aclocal" || mkdir -p -- "/usr/share/aclocal"
 /usr/bin/install -c -m 644 'alsa.m4' '/usr/share/aclocal/alsa.m4'
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'alsa.pc' '/usr/lib/pkgconfig/alsa.pc'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/utils'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16/utils'
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16'
make[2]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[2]: Für das Ziel »install-data-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-lib-1.0.16'
Compile ALSA Utility......
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.15... found.
checking for snd_ctl_open in -lasound... yes
checking for snd_tlv_get_dB_range... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating alsactl/Makefile
config.status: creating alsamixer/Makefile
config.status: creating amidi/Makefile
config.status: creating amixer/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating alsaconf/alsaconf
config.status: creating alsaconf/Makefile
config.status: creating alsaconf/po/Makefile
config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting
config.status: creating aplay/Makefile
config.status: creating include/Makefile
config.status: creating iecset/Makefile
config.status: creating utils/Makefile
config.status: creating utils/alsa-utils.spec
config.status: creating seq/Makefile
config.status: creating seq/aconnect/Makefile
config.status: creating seq/aplaymidi/Makefile
config.status: creating seq/aseqdump/Makefile
config.status: creating seq/aseqnet/Makefile
config.status: creating speaker-test/Makefile
config.status: creating speaker-test/samples/Makefile
config.status: creating include/aconfig.h
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands
Making all in include
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/include'
make  all-am
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/include'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/include'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/include'
Making all in alsactl
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
	then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
	then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT names.o -MD -MP -MF ".deps/names.Tpo" -c -o names.o names.c; \
	then mv -f ".deps/names.Tpo" ".deps/names.Po"; else rm -f ".deps/names.Tpo"; exit 1; fi
gcc  -g -O2   -o alsactl  alsactl.o state.o names.o  -lasound -lm -ldl -lpthread
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsactl'
Making all in alsaconf
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf'
Making all in po
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf/po'
mv: Aufruf von stat für „t-ja.gmo“ nicht möglich: No such file or directory
make[2]: *** [ja.gmo] Fehler 1
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf'
make: *** [all-recursive] Fehler 1
Making install in include
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/include'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/include'
make[2]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[2]: Für das Ziel »install-data-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/include'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/include'
Making install in alsactl
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsactl'
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsactl'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsactl'
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsactl'
Making install in alsaconf
make[1]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf'
Making install in po
make[2]: Betrete Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf/po'
mv: Aufruf von stat für „t-ja.gmo“ nicht möglich: No such file or directory
[color=#DA0000]make[2]: *** [ja.gmo] Fehler 1[/color]
make[2]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf/po'
[color=#DA0000]make[1]: *** [install-recursive] Fehler 1[/color]
make[1]: Verlasse Verzeichnis '/home/johannes/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf'
[color=#DA0000]make: *** [install-recursive] Fehler 1[/color]
Remove Folder.....
[color=#DA0000]./install: 101: alsaconf: not found[/color]
johannes@johann-4:~/Desktop/realtek-linux-audiopack-5.07$ 
```

When I start the old kernel, the sound works. With the new one, I get an error when I click on the volume slider (left to the clock) saying, that there is no sound device. "alsamixer" in the cosole prints an error too. 

So what can I do? 
Thx,
Johannes

---

### Post by indecisive on 2009-01-29
First, if you are using Ubuntu, you will compile and install the driver manually.  Read the INSTALL file.  Otherwise, I am having trouble after updating my kernel, and can not find alsaconf anywhere.

---

