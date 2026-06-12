---
title: "Audio is quiet - sound through headphones is almost silent."
date: 2010-06-27
forum: Hardware
---

### Post by macgeek417 on 2010-06-27
Hello, I recently got a new computer (a Samsung NP-Q430, laptop) with the following specs:
Intel Core i5
4GB RAM
500GB HD
Nvidia 310M 512MB graphics

According to aplay -l, my sound card is:
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]

On my old (crappy) laptop, I had to keep the audio at a very low level (like 3%) to not have it blast my ears off, but on this one, even through the speakers I need it at 75% to be a decent volume.

Any ideas? Is there some sort of preamp I can enable?

---

### Post by macgeek417 on 2010-06-28
Bumppity bump.

---

### Post by 23dornot23d on 2010-06-28
Hi ..... I have just spent quite a lot of time tracking down sound problems on the latest version of Ubuntu .... 

Though this is not the same as your problem, all the commands and the tracking the problem down are there ......

It may take a bit of trawling through ,,,, but have a look and run alsamixer from a terminal

just to check that all your levels are ok to start with ..... basic I know ..... but sometimes
it can be the simplest of things ...... in my case though it was not ..... and had to edit the
alsa config file to add a line to it .......... thats at the very end of this thread.

Have a good look through it and do not remove any drivers or anything .....

Just see if you can find anything simple first ..... and then maybe alter the config file at the end of

the thread as I did ...... you can always alter it back easily if it does not solve your problem

[Sound Problems Solved]("http://ubuntuforums.org/showthread.php?t=1515200") 

Hope it helps .....

---

### Post by macgeek417 on 2010-06-28
All of my volume controls are allready at the max in alsamixer. I have also edited /etc/modprobe.d/alsa-base.conf to add 'options snd-hda-intel model=basic' but that simply breaks it further - It causes it to not sense when headphones are plugged in and does not play sound through the headphones.

I have read that updating ALSA can possibly fix the problem. I will try this and post back.

:)

---

### Post by macgeek417 on 2010-06-28
Updating ALSA to 1.0.23 has fixed the problem.

I followed the tutorial here: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) to update it.

---

### Post by 23dornot23d on 2010-06-28
Thats the way I do it nearly every new version of Ubuntu .... compile the latest Alsa ...
Glad you got it fixed ..... 
I tried compiling it in Maverick and ran into problems ....
So do a good check on this before upgrading as you may lose it again .......... and I am
not sure about how easy it will be to sort out ..... but there is a way to go yet before 
Maverick is released ......

---

### Post by macgeek417 on 2010-06-28
Just out of curriosity, exactly what problems did you run in to when trying to compile under Maverick?

---

### Post by 23dornot23d on 2010-06-29
When I try to make the Alsa Drivers ......

The ./configure seems to be ok
```

root@keith-laptop:/usr/src/alsa/alsa-driver-1.0.23# ./configure
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.23
checking cross compile... 
checking for directory with ALSA kernel sources... ../alsa-kmirror
checking for directory with kernel source... /lib/modules/2.6.35-6-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h ... linux/version.h
checking for kernel linux/autoconf.h generated/autoconf.h... generated/autoconf.h
checking for kernel linux/utsrelease.h generated/utsrelease.h... generated/utsrelease.h
checking for kernel version... 2.6.35-6-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (Ubuntu 4.4.4-6ubuntu1) 4.4.4

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
checking for directory to store kernel modules... /lib/modules/2.6.35-6-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for ISA DMA API... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... no
Creating a dummy <linux/utsrelease.h>...
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
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
checking for kernel linux/io.h... yes
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
checking for kernel linux/debugfs.h... yes
checking for kernel linux/gpio.h... yes
checking for kernel linux/bug.h... yes
checking for kernel linux/math64.h... yes
checking for kernel linux/regulator/consumer.h... yes
checking for kernel linux/dmi.h... yes
checking for kernel linux/bitrev.h... yes
checking for kernel linux/hrtimer.h... yes
checking for kernel linux/gcd.h... yes
checking for kernel linux/gfp.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker platform in kernel... yes
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
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... yes
checking for video_drvdata... yes
checking for V4L1 layer... yes
checking for V4L2 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kstrndup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for pci_ioremap_bar... yes
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.23
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for kernel linux/usb/audio-v2.h... yes
checking for kernel linux/usb/audio.h... yes
checking for valid v1 in linux/usb/audio.h... no
Creating <linux/usb/audio.h>...
checking for kernel linux/usb/ch9.h... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... yes
checking for builtin _Bool support... yes
checking for x86-compatible PC... no
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... all
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
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
root@keith-laptop:/usr/src/alsa/alsa-driver-1.0.23# 


```But then the make fails with a error

```

Hunk #2 succeeded at 835 (offset 1 line).
Hunk #3 succeeded at 1094 (offset 1 line).
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
Hunk #2 succeeded at 612 (offset 1 line).
Hunk #3 succeeded at 883 (offset 1 line).
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/mpu401'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #2 succeeded at 438 (offset 2 lines).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl4'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl4'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/pcsp'
copying file alsa-kernel/drivers/pcsp/pcsp.c
patching file pcsp.c
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/pcsp'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1848'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1848'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/cs423x'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/cs423x'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/es1688'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/es1688'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/gus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/gus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/msnd'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/msnd'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
Hunk #2 succeeded at 712 (offset 2 lines).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/sb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
Hunk #2 succeeded at 251 (offset -3 lines).
copying file alsa-kernel/isa/wavefront/wavefront_synth.c
patching file wavefront_synth.c
Hunk #2 succeeded at 1947 (offset 1 line).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wavefront'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wss'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/synth'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/synth/emux'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/synth/emux'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/synth'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
copying file alsa-kernel/pci/atiixp.c
patching file atiixp.c
Hunk #2 succeeded at 1680 (offset 9 lines).
Hunk #3 succeeded at 1725 (offset 9 lines).
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c
Hunk #2 succeeded at 1313 (offset 6 lines).
Hunk #3 succeeded at 1356 (offset 6 lines).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #2 succeeded at 850 (offset 4 lines).
Hunk #3 succeeded at 1004 (offset 4 lines).
copying file alsa-kernel/pci/cmipci.c
patching file cmipci.c
Hunk #2 succeeded at 3142 (offset -34 lines).
Hunk #3 succeeded at 3437 (offset -34 lines).
copying file alsa-kernel/pci/ens1370.c
patching file ens1370.c
Hunk #2 succeeded at 2121 (offset -10 lines).
Hunk #3 succeeded at 2497 (offset -10 lines).
copying file alsa-kernel/pci/fm801.c
patching file fm801.c
Hunk #3 succeeded at 1434 (offset 5 lines).
Hunk #4 succeeded at 1624 (offset 14 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #3 succeeded at 715 (offset 9 lines).
Hunk #4 succeeded at 725 (offset 9 lines).
Hunk #5 succeeded at 3288 (offset 160 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
copying file alsa-kernel/pci/via82xx.c
patching file via82xx.c
Hunk #2 succeeded at 2500 (offset 6 lines).
Hunk #3 succeeded at 2510 (offset 6 lines).
Hunk #4 succeeded at 2525 (offset 6 lines).
Hunk #5 succeeded at 2536 (offset 6 lines).
Hunk #6 succeeded at 2547 (offset 6 lines).
Hunk #7 succeeded at 2630 (offset 6 lines).
copying file alsa-kernel/pci/via82xx_modem.c
patching file via82xx_modem.c
Hunk #2 succeeded at 1187 (offset 7 lines).
Hunk #3 succeeded at 1247 (offset 7 lines).
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #3 succeeded at 1928 (offset 10 lines).
Hunk #4 succeeded at 1940 (offset 10 lines).
Hunk #5 succeeded at 1964 (offset 10 lines).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ac97'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ali5451'
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c
Hunk #2 succeeded at 2148 (offset -57 lines).
Hunk #3 succeeded at 2318 (offset -57 lines).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ali5451'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/asihpi'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/asihpi'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/au88x0'
copying file alsa-kernel/pci/au88x0/au88x0.c
patching file au88x0.c
Hunk #2 succeeded at 339 (offset -2 lines).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/au88x0'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/aw2'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/aw2'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ca0106'
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c
Hunk #3 succeeded at 1636 (offset 73 lines).
Hunk #4 succeeded at 1908 (offset 83 lines).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ca0106'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ctxfi'
copying file alsa-kernel/pci/ctxfi/ctatc.c
patching file ctatc.c
Hunk #2 succeeded at 1238 (offset -10 lines).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ctxfi'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1945 (offset 2 lines).
Hunk #2 succeeded at 2017 (offset 2 lines).
Hunk #3 succeeded at 2252 (offset 1 line).
Hunk #4 succeeded at 2260 (offset 1 line).
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
copying file alsa-kernel/pci/echoaudio/indigodjx.c
patching file indigodjx.c
Hunk #2 succeeded at 112 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/indigoiox.c
patching file indigoiox.c
Hunk #2 succeeded at 114 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
Hunk #2 succeeded at 125 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/echoaudio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #4 succeeded at 1409 (offset -1 lines).
Hunk #5 succeeded at 1452 (offset -1 lines).
Hunk #6 succeeded at 1767 (offset 3 lines).
copying file alsa-kernel/pci/emu10k1/emu10k1x.c
patching file emu10k1x.c
Hunk #2 succeeded at 941 (offset 1 line).
Hunk #3 succeeded at 1634 (offset 6 lines).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/emu10k1'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/hda'
copying file alsa-kernel/pci/hda/hda_intel.c
patching file hda_intel.c
Hunk #2 succeeded at 2360 (offset 7 lines).
Hunk #3 succeeded at 2376 (offset 8 lines).
Hunk #4 succeeded at 2392 (offset 8 lines).
Hunk #5 succeeded at 2405 (offset 8 lines).
Hunk #6 succeeded at 2526 (offset 8 lines).
copying file alsa-kernel/pci/hda/hda_beep.c
patching file hda_beep.c
Hunk #2 succeeded at 95 (offset 1 line).
Hunk #3 succeeded at 123 with fuzz 2 (offset 1 line).
Hunk #4 succeeded at 141 (offset 1 line).
Hunk #5 succeeded at 163 (offset 1 line).
Hunk #6 succeeded at 282 with fuzz 2 (offset 18 lines).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/hda'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ice1712'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ice1712'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #2 succeeded at 2344 (offset 5 lines).
Hunk #3 succeeded at 2500 (offset 5 lines).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/korg1212'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/mixart'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/mixart'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/nm256'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/nm256'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/oxygen'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/oxygen'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pdplus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pdplus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #3 succeeded at 2221 (offset 3 lines).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/riptide'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/rme9652'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/rme9652'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/trident'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/trident'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/vx222'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/vx222'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ymfpci'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/core'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/core'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc'
copying file alsa-kernel/soc/soc-core.c
patching file soc-core.c
Hunk #2 succeeded at 1331 (offset 90 lines).
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/atmel'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/atmel'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/au1x'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/au1x'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/blackfin'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/blackfin'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/davinci'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/davinci'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/fsl'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/fsl'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/imx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/imx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/omap'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/omap'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/pxa'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/pxa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s6000'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s6000'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/sh'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/sh'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/txx9'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/txx9'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb'
copying file alsa-kernel/usb/card.c
patching file card.c
copying file alsa-kernel/usb/endpoint.c
patching file endpoint.c
Hunk #2 succeeded at 187 (offset 2 lines).
Hunk #3 succeeded at 278 (offset 2 lines).
Hunk #4 succeeded at 309 (offset 2 lines).
copying file alsa-kernel/usb/helper.c
patching file helper.c
Hunk #2 succeeded at 93 (offset 1 line).
copying file alsa-kernel/usb/quirks.c
patching file quirks.c
Hunk #2 succeeded at 161 (offset 2 lines).
Hunk #3 succeeded at 236 (offset 2 lines).
Hunk #4 succeeded at 325 (offset 2 lines).
Hunk #5 succeeded at 343 (offset 2 lines).
Hunk #6 succeeded at 357 (offset 2 lines).
Hunk #7 succeeded at 370 (offset 2 lines).
copying file alsa-kernel/usb/urb.c
patching file urb.c
Hunk #2 succeeded at 72 (offset 1 line).
Hunk #3 succeeded at 87 (offset 1 line).
Hunk #4 succeeded at 171 (offset 1 line).
Hunk #5 succeeded at 198 (offset 1 line).
Hunk #6 succeeded at 350 (offset 1 line).
copying file alsa-kernel/usb/midi.c
patching file midi.c
Hunk #6 succeeded at 1004 with fuzz 1.
Hunk #7 succeeded at 1021 (offset 2 lines).
Hunk #8 succeeded at 1031 (offset 2 lines).
Hunk #9 succeeded at 1749 (offset 12 lines).
Hunk #10 succeeded at 2120 (offset 12 lines).
copying file alsa-kernel/usb/mixer.c
patching file mixer.c
copying file alsa-kernel/usb/mixer_quirks.c
patching file mixer_quirks.c
Hunk #2 succeeded at 64 (offset 1 line).
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb/caiaq'
copying file alsa-kernel/usb/caiaq/audio.c
patching file audio.c
Hunk #2 succeeded at 465 (offset 1 line).
Hunk #3 succeeded at 528 (offset 1 line).
copying file alsa-kernel/usb/caiaq/device.c
patching file device.c
Hunk #2 succeeded at 139 (offset 7 lines).
Hunk #3 succeeded at 401 (offset 7 lines).
copying file alsa-kernel/usb/caiaq/input.c
patching file input.c
Hunk #2 succeeded at 21 with fuzz 1 (offset 1 line).
Hunk #3 succeeded at 301 (offset 1 line).
Hunk #4 succeeded at 322 (offset 1 line).
Hunk #5 succeeded at 364 (offset 1 line).
Hunk #6 succeeded at 378 (offset 1 line).
Hunk #7 succeeded at 507 (offset 1 line).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb/caiaq'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb/misc'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb/misc'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
Hunk #2 succeeded at 33 (offset 1 line).
Hunk #3 succeeded at 56 (offset 1 line).
Hunk #4 succeeded at 142 (offset 1 line).
Hunk #5 succeeded at 181 (offset 1 line).
Hunk #6 succeeded at 237 (offset 1 line).
Hunk #7 succeeded at 290 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
Hunk #2 succeeded at 174 (offset 1 line).
Hunk #3 succeeded at 190 (offset 1 line).
Hunk #4 succeeded at 254 (offset 1 line).
Hunk #5 succeeded at 267 (offset 1 line).
Hunk #6 succeeded at 313 (offset 1 line).
Hunk #7 succeeded at 377 (offset 1 line).
Hunk #8 succeeded at 401 (offset 1 line).
Hunk #9 succeeded at 427 (offset 1 line).
Hunk #10 succeeded at 448 (offset 1 line).
Hunk #11 succeeded at 508 (offset 1 line).
Hunk #12 succeeded at 528 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #2 succeeded at 69 (offset 1 line).
Hunk #3 succeeded at 317 (offset 1 line).
Hunk #4 succeeded at 350 (offset 1 line).
Hunk #5 succeeded at 366 (offset 1 line).
Hunk #6 succeeded at 392 (offset 1 line).
Hunk #7 succeeded at 408 (offset 1 line).
Hunk #8 succeeded at 525 (offset 1 line).
Hunk #9 succeeded at 548 (offset 1 line).
Hunk #10 succeeded at 697 (offset 1 line).
Hunk #11 succeeded at 1061 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
Hunk #2 succeeded at 153 (offset 1 line).
Hunk #3 succeeded at 233 (offset 1 line).
Hunk #4 succeeded at 267 (offset 1 line).
Hunk #5 succeeded at 307 (offset 1 line).
Hunk #6 succeeded at 328 (offset 1 line).
Hunk #7 succeeded at 454 (offset 1 line).
Hunk #8 succeeded at 482 (offset 1 line).
Hunk #9 succeeded at 715 (offset 1 line).
Hunk #10 succeeded at 728 (offset 1 line).
Hunk #11 succeeded at 803 (offset 1 line).
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb/usx2y'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/misc'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/misc'
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23'
make -C /lib/modules/2.6.35-6-generic/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.23  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-6-generic'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.23/acore/hrtimer.o
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/adriver.h:25,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/hrtimer.c:1:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175:1: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
In file included from <command-line>:0:
./include/generated/autoconf.h:2223:1: warning: this is the location of the previous definition
  CC [M]  /usr/src/alsa/alsa-driver-1.0.23/acore/hwdep.o
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/adriver.h:25,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/hwdep.c:1:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175:1: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
In file included from <command-line>:0:
./include/generated/autoconf.h:2223:1: warning: this is the location of the previous definition
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/adriver.h:25,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/hwdep.c:1:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175:1: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
In file included from <command-line>:0:
./include/generated/autoconf.h:2223:1: warning: this is the location of the previous definition
  CC [M]  /usr/src/alsa/alsa-driver-1.0.23/acore/memory_wrapper.o
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/memory_wrapper.c:1:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175:1: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
In file included from <command-line>:0:
./include/generated/autoconf.h:2223:1: warning: this is the location of the previous definition
  CC [M]  /usr/src/alsa/alsa-driver-1.0.23/acore/memalloc.o
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/memalloc.inc:1,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175:1: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
In file included from <command-line>:0:
./include/generated/autoconf.h:2223:1: warning: this is the location of the previous definition
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/memalloc.inc:1,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175:1: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
In file included from <command-line>:0:
./include/generated/autoconf.h:2223:1: warning: this is the location of the previous definition
  CC [M]  /usr/src/alsa/alsa-driver-1.0.23/acore/sgbuf.o
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/sgbuf.c:1:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175:1: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
In file included from <command-line>:0:
./include/generated/autoconf.h:2223:1: warning: this is the location of the previous definition
  CC [M]  /usr/src/alsa/alsa-driver-1.0.23/acore/pcm.o
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/adriver.h:25,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/pcm.c:1:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175:1: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
In file included from <command-line>:0:
./include/generated/autoconf.h:2223:1: warning: this is the location of the previous definition
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/adriver.h:25,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/pcm.c:1:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175:1: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
In file included from <command-line>:0:
./include/generated/autoconf.h:2223:1: warning: this is the location of the previous definition
  CC [M]  /usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.o
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/adriver.h:25,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c:2:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175:1: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
In file included from <command-line>:0:
./include/generated/autoconf.h:2223:1: warning: this is the location of the previous definition
/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c: In function &#8216;snd_pcm_hw_params&#8217;:
/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c:489: error: implicit declaration of function &#8216;pm_qos_remove_requirement&#8217;
/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function &#8216;pm_qos_add_requirement&#8217;
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-6-generic'
make: *** [compile] Error 2
root@keith-laptop:/usr/src/alsa/alsa-driver-1.0.23# 

```I get the errors above .......


I did a search as I always do to see how others solved this ..... but it seems to be to use a older kernel

not the solution I want ......... [Solutions]("http://www.google.com/search?hl=en&q=%2Facore%2Fpcm_native.o+Error+1+solved&cts=1277796620756&aq=f&aqi=&aql=&oq=&gs_rfai=")

Also tried [POST 1313 HERE]("http://ohioloco.ubuntuforums.org/showthread.php?t=205449&page=132")
to get back to the initial drivers ....... without doing a full re-install of the System ........... but it failed too ...

---

