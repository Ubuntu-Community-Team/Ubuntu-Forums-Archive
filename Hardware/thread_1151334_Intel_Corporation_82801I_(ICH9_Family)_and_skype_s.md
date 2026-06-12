---
title: "Intel Corporation 82801I (ICH9 Family) and skype sound wont work HELP"
date: 2009-05-06
forum: Hardware
---

### Post by koco on 2009-05-06
Hi there guys, I'm newbie in linux ubuntu 9.04 and i got problem with my sound on my acer aspire 7730 i can play movies and mp3 and so on but when i like to use skype it wont work for me properly. I can hear sound but no one can hear me it looks like my mic is not detected properly or some thing like that.  i have this sound card Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) and i'm using HDA intel alsa mixer every thing looks fine mic and so on are enabled. I tryed to install new alsa driver but i couldnt finish instalation for some reason, just have dificulties to install tar.gz2 this is what i got :

babinoha@babinoha-laptop:~$ cd /home/babinoha/Plocha/alsa
babinoha@babinoha-laptop:~/Plocha/alsa$ ./configure
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
checking for current directory... /home/babinoha/Plocha/alsa
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.28-11-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.28-11-generic
checking for GCC version... ./configure: eval: line 5233: syntax error near unexpected token `)'
./configure: eval: line 5233: `my_compiler_version=4.3.3-5ubuntu4)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3

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
checking for directory to store kernel modules... /lib/modules/2.6.28-11-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
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
checking for tty->count is the atomic type... no
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
checking for driver version... 1.0.20
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
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... yes
checking for builtin _Bool support... yes
checking for x86-compatible PC... yes
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
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
babinoha@babinoha-laptop:~/Plocha/alsa$ make
if [ ! -d include/sound -a ! -L include/sound ]; then \
      ln -sf ../alsa-kernel/include include/sound ; \
    fi
cp -puvf include/version.h include/sound/version.h
„include/version.h“ -> „include/sound/version.h“
make dep
make[1]: Entering directory `/home/babinoha/Plocha/alsa'
make[2]: Entering directory `/home/babinoha/Plocha/alsa/acore'
copying file alsa-kernel/core/info.c
/home/babinoha/Plocha/alsa/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/babinoha/Plocha/alsa/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/babinoha/Plocha/alsa'
make: *** [include/sndversions.h] Error 2
babinoha@babinoha-laptop:~/Plocha/alsa$ make install
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /home/babinoha/Plocha/alsa/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
rm: nelze odstranit „/usr/include/sound/hdsp.h“: Permission denied
rm: nelze odstranit „/usr/include/sound/sfnt_info.h“: Permission denied
rm: nelze odstranit „/usr/include/sound/asound_fm.h“: Permission denied
rm: nelze odstranit „/usr/include/sound/asound.h“: Permission denied
rm: nelze odstranit „/usr/include/sound/sscape_ioctl.h“: Permission denied
rm: nelze odstranit „/usr/include/sound/sb16_csp.h“: Permission denied
rm: nelze odstranit „/usr/include/sound/asequencer.h“: Permission denied
rm: nelze odstranit „/usr/include/sound/emu10k1.h“: Permission denied
rm: nelze odstranit „/usr/include/sound/hdspm.h“: Permission denied
install: cannot create regular file „/usr/include/sound/ac97_codec.h“: Permission denied
install: cannot create regular file „/usr/include/sound/ad1816a.h“: Permission denied
install: cannot create regular file „/usr/include/sound/ad1843.h“: Permission denied
install: cannot create regular file „/usr/include/sound/ak4114.h“: Permission denied
install: cannot create regular file „/usr/include/sound/ak4117.h“: Permission denied
install: cannot create regular file „/usr/include/sound/ak4531_codec.h“: Permission denied
install: cannot create regular file „/usr/include/sound/ak4xxx-adda.h“: Permission denied
install: nelze odstranit „/usr/include/sound/asequencer.h“: Permission denied
install: nelze odstranit „/usr/include/sound/asound.h“: Permission denied
install: nelze odstranit „/usr/include/sound/asound_fm.h“: Permission denied
install: cannot create regular file „/usr/include/sound/asoundef.h“: Permission denied
install: cannot create regular file „/usr/include/sound/atmel-abdac.h“: Permission denied
install: cannot create regular file „/usr/include/sound/atmel-ac97c.h“: Permission denied
install: cannot create regular file „/usr/include/sound/control.h“: Permission denied
install: cannot create regular file „/usr/include/sound/core.h“: Permission denied
install: cannot create regular file „/usr/include/sound/cs4231-regs.h“: Permission denied
install: cannot create regular file „/usr/include/sound/cs46xx.h“: Permission denied
install: cannot create regular file „/usr/include/sound/cs46xx_dsp_scb_types.h“: Permission denied
install: cannot create regular file „/usr/include/sound/cs46xx_dsp_spos.h“: Permission denied
install: cannot create regular file „/usr/include/sound/cs46xx_dsp_task_types.h“: Permission denied
install: cannot create regular file „/usr/include/sound/cs8403.h“: Permission denied
install: cannot create regular file „/usr/include/sound/cs8427.h“: Permission denied
install: cannot create regular file „/usr/include/sound/driver.h“: Permission denied
install: nelze odstranit „/usr/include/sound/emu10k1.h“: Permission denied
install: cannot create regular file „/usr/include/sound/emu10k1_synth.h“: Permission denied
install: cannot create regular file „/usr/include/sound/emu8000.h“: Permission denied
install: cannot create regular file „/usr/include/sound/emu8000_reg.h“: Permission denied
install: cannot create regular file „/usr/include/sound/emux_legacy.h“: Permission denied
install: cannot create regular file „/usr/include/sound/emux_synth.h“: Permission denied
install: cannot create regular file „/usr/include/sound/es1688.h“: Permission denied
install: cannot create regular file „/usr/include/sound/gus.h“: Permission denied
install: cannot create regular file „/usr/include/sound/hda_hwdep.h“: Permission denied
install: nelze odstranit „/usr/include/sound/hdsp.h“: Permission denied
install: nelze odstranit „/usr/include/sound/hdspm.h“: Permission denied
install: cannot create regular file „/usr/include/sound/hwdep.h“: Permission denied
install: cannot create regular file „/usr/include/sound/i2c.h“: Permission denied
install: cannot create regular file „/usr/include/sound/info.h“: Permission denied
install: cannot create regular file „/usr/include/sound/initval.h“: Permission denied
install: cannot create regular file „/usr/include/sound/jack.h“: Permission denied
install: cannot create regular file „/usr/include/sound/l3.h“: Permission denied
install: cannot create regular file „/usr/include/sound/memalloc.h“: Permission denied
install: cannot create regular file „/usr/include/sound/minors.h“: Permission denied
install: cannot create regular file „/usr/include/sound/mixer_oss.h“: Permission denied
install: cannot create regular file „/usr/include/sound/mpu401.h“: Permission denied
install: cannot create regular file „/usr/include/sound/opl3.h“: Permission denied
install: cannot create regular file „/usr/include/sound/opl4.h“: Permission denied
install: cannot create regular file „/usr/include/sound/pcm-indirect.h“: Permission denied
install: cannot create regular file „/usr/include/sound/pcm.h“: Permission denied
install: cannot create regular file „/usr/include/sound/pcm_oss.h“: Permission denied
install: cannot create regular file „/usr/include/sound/pcm_params.h“: Permission denied
install: cannot create regular file „/usr/include/sound/pt2258.h“: Permission denied
install: cannot create regular file „/usr/include/sound/pxa2xx-lib.h“: Permission denied
install: cannot create regular file „/usr/include/sound/rawmidi.h“: Permission denied
install: cannot create regular file „/usr/include/sound/s3c24xx_uda134x.h“: Permission denied
install: cannot create regular file „/usr/include/sound/sb.h“: Permission denied
install: nelze odstranit „/usr/include/sound/sb16_csp.h“: Permission denied
install: cannot create regular file „/usr/include/sound/seq_device.h“: Permission denied
install: cannot create regular file „/usr/include/sound/seq_kernel.h“: Permission denied
install: cannot create regular file „/usr/include/sound/seq_midi_emul.h“: Permission denied
install: cannot create regular file „/usr/include/sound/seq_midi_event.h“: Permission denied
install: cannot create regular file „/usr/include/sound/seq_oss.h“: Permission denied
install: cannot create regular file „/usr/include/sound/seq_oss_legacy.h“: Permission denied
install: cannot create regular file „/usr/include/sound/seq_virmidi.h“: Permission denied
install: nelze odstranit „/usr/include/sound/sfnt_info.h“: Permission denied
install: cannot create regular file „/usr/include/sound/snd_wavefront.h“: Permission denied
install: cannot create regular file „/usr/include/sound/soc-dai.h“: Permission denied
install: cannot create regular file „/usr/include/sound/soc-dapm.h“: Permission denied
install: cannot create regular file „/usr/include/sound/soc-of-simple.h“: Permission denied
install: cannot create regular file „/usr/include/sound/soc.h“: Permission denied
install: cannot create regular file „/usr/include/sound/soundfont.h“: Permission denied
install: nelze odstranit „/usr/include/sound/sscape_ioctl.h“: Permission denied
install: cannot create regular file „/usr/include/sound/tea575x-tuner.h“: Permission denied
install: cannot create regular file „/usr/include/sound/tea6330t.h“: Permission denied
install: cannot create regular file „/usr/include/sound/timer.h“: Permission denied
install: cannot create regular file „/usr/include/sound/tlv.h“: Permission denied
install: cannot create regular file „/usr/include/sound/trident.h“: Permission denied
install: cannot create regular file „/usr/include/sound/uda134x.h“: Permission denied
install: cannot create regular file „/usr/include/sound/util_mem.h“: Permission denied
install: cannot create regular file „/usr/include/sound/version.h“: Permission denied
install: cannot create regular file „/usr/include/sound/vx_core.h“: Permission denied
install: cannot create regular file „/usr/include/sound/wavefront.h“: Permission denied
install: cannot create regular file „/usr/include/sound/wss.h“: Permission denied
install: cannot create regular file „/usr/include/sound/ymfpci.h“: Permission denied
make: *** [install-headers] Error 1
babinoha@babinoha-laptop:~/Plocha/alsa$ make 
make dep
make[1]: Entering directory `/home/babinoha/Plocha/alsa'
make[2]: Entering directory `/home/babinoha/Plocha/alsa/acore'
copying file alsa-kernel/core/info.c
/home/babinoha/Plocha/alsa/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/babinoha/Plocha/alsa/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/babinoha/Plocha/alsa'
make: *** [include/sndversions.h] Error 2
babinoha@babinoha-laptop:~/Plocha/alsa$ 

I'm not sure what i'm doing just guessing. I checked already all settings in skype but non of them worked. one more thing is ripping my head of:  no jack output at all.
please help me someone as sound is importent for me and bloode skype as well 

thank's lot 
excuse my english too.  :-)

---

### Post by dunbrokin on 2009-06-25
Since the latest update, I have the same problem.....Skype seems screwed up. I can hear them but they cannot hear me...we can both see each other o video....weird.

---

