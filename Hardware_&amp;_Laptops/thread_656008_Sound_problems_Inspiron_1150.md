---
title: "Sound problems Inspiron 1150"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by mlorsung on 2008-01-02
ok--I am completely frustrated and feel as though I have tried nearly everything I can think of...  The issue is this--I have been running Ubuntu 7.0.4 for almost a year now with no issues, everything except my USB wifi card worked out of the box and even that was pretty simple to setup with ndiswrapper...  A couple of days ago, I got home from work and thought "gee, Id like to watch some episodes of my favorite television show...." so I fired up VLC and hit play--to my dismay I suddenly lack sound in any capacity...  nothing plays, though I seem to have drivers installed, and AFAIK nothing has changed on my system...  I read through and followed most of the comprehensive sound problems guide on here to no avail...  so Im turning to the forums users to help me figure this out, hopefully its something incredibly simple that Ive been missing.  Below is the information on my system and sound card, any and all help is appreciated.

-michael

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [Intel 82801DB-ICH4 Modem], device 0: Intel ICH - Modem [Intel 82801DB-ICH4 Modem - Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```

lspci -v

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell Unknown device 017f
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at c800 [size=256]
        I/O ports at cc40 [size=64]
        Memory at f6eff800 (32-bit, non-prefetchable) [size=512]
        Memory at f6eff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
```



hope this helps, and can help me

-michael

---

### Post by balaknair on 2008-01-02
I had a few issues with my HDA card under Feisty and Gutsy too, with similar problems as you have outlined. This is what worked for me.
It could be that your sound card codec is just not being loaded(at least that's what I think I mean)

open a terminal and enter the following command

```
cat /proc/asound/card0/codec#* | grep Codec

```
this will tell you what codec your sound card type needs
for eg my card returned "Codec: Analog Devices AD1986A"
so the card I use is AD1986A
Next find your card configuration by checking the following link
[http://www.mjmwired.net/kernel/Docum...figuration.txt](http://www.mjmwired.net/kernel/Docum...figuration.txt)

(the alsa-config should also be on your system at usr/src/(your kernel version)/sound/alsa/alsa-configuration.txt)

in that page find your card model and check the details given
eg
```
AD1986A
919 6stack 6-jack, separate surrounds (default)
920 3stack 3-stack, shared surrounds
921 laptop 2-channel only (FSC V2060, Samsung M50)
922 laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
923 ultra 2-channel with EAPD (Samsung Ultra tablet PC)
```

select the description that best matches your system(eg a 5.1 surround system with 6 audio-out channels/ports would be 6stack)

then go back to the terminal and type

```
sudo nano /etc/modprobe.d/alsa-base
```

Paste this into the last line of the file
Code:

```
options snd-hda-intel model=MODEL

```
replace MODEL with your model(6stack, 3stack, laptop etc.)

reboot.

if this doesn't work you might have to consider recompiling the alsa-kernel(though if you followed the ubuntuforums guides I guess you've already tried it.

These steps are just a part of the howto guide at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I've only mentioned the steps that worked for me with the HDA-Intel card(like ICH8 ) with Gutsy 7.04, 7.10, and with Mandriva 2008- recompiling the kernel with Gutsy led to my sound card not being detected at all and I had to purge alsa and try again, that's why I mentioned just the tips that worked for me.

Lotsa luck

---

### Post by mlorsung on 2008-01-02
when I input "cat /proc/asound/card0/codec#* | grep Codec"
I get: "cat: /proc/asound/card0/codec#*: No such file or directory"


not sure why that is--any ideas?
-michael

---

### Post by balaknair on 2008-01-02
Not too sure, maybe the file was accidentally deleted? how about trying the command without the #?
I just entered that in a terminal, got the proper response.

wanted to add a couple of things
I just checked the alsa-project site, the ICH4 uses the snd-intel8x0m module.
so once you get [cat /proc/asound/card0/codec#* | grep Codec] working replace the snd-hda-intel with snd-intel8x0m in modprobe

---

### Post by mlorsung on 2008-01-05
ok, so when i do modprobe i get

```
WARNING: /etc/modprobe.d/alsa-base.save line 1: ignoring bad line starting with 'c#'
FATAL: Module snd_snd_intel8x0 not found.

```

i am at my wits end!  please, anyone, please help!

---

### Post by balaknair on 2008-01-05
copy paste error
it should be snd-intel8x0m, not snd-snd-intel8x0m
and be sure to paste it at the end of the file
hope this fixes your problems

options snd-intel8x0 model=MODEL

where MODEL is the model descriptionin alsa-configuration.txt that matches your set-up.

---

### Post by balaknair on 2008-01-05
I also found this at the Comprehensive sound guide
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[I] * webbca01 figured out how to get AC'97 work with the help of the second last post here {http://www.linuxforum.com/forums/index.php/topic,178761.new/topicseen.html}  and this post {http://ubuntuforums.org/showthread.php?t=14989}. Basically, if you have an intel8x0 module, you can get AC'97 working by
    sudo nano /etc/modprobe.d/alsa-base

      and adding this as the last line:
       options snd-intel8x0 ac97_quirk=3[/I]

and restart your sound system

Try it if the previous steps don't work for you

It's 3:00 AM here now, and I really need to get some sleep. Will check back tomorrow morning for sure
Please do let me know if you manage to get your sound problem straightened out(and just what the steps which worked were)
Wishing you luck

---

### Post by mlorsung on 2008-01-06
fixed my typo, i still get the following when i type "sudo modprobe snd-intel8x0m"

```
WARNING: /etc/modprobe.d/alsa-base.save line 1: ignoring bad line starting with 'c#'

```

//edit//
so I decided to try following the comprehensive sound guide from start to finish again, in case i missed something...  I completed everything including recompiling drivers, etc and now when i type "alsamixer" i get 
```
"alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB, version ALSA_0.9 not defined in file libasound.so.2 with link time reference"

```

this is completely got me baffled, is there anyone else out there who can help me?  I dont understand why for months ubuntu has been running great for me, sound and all (out of the box, no less!) and now it just decides to break!

---

### Post by mlorsung on 2008-01-06
ok-so ive gone through the comprehensive troubleshooting guide again--when it came to recompiling the drivers i selected intel8x0, and it errored--the output from the log is below, perhaps this will help clarify the issues im having?  Im almost positive its just a driver issue, and im sure its something silly im doing.  Thanks again!

Michael

buildlog:

```

for i in control postinst postrm ; do \
		if [ -f debian/$i.orig ]; then \
			mv -f debian/$i.orig debian/$i ; \
		fi ; \
	done
rm -f control-munge
make mrproper
make[1]: Entering directory `/usr/src/modules/alsa-driver'
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[2]: Entering directory `/usr/src/modules/alsa-driver/acore'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
rm -f configure-stamp
rm -f build-stamp
/usr/bin/make -f debian/rules binary-modules
make[1]: Entering directory `/usr/src/modules/alsa-driver'
CC="gcc-4.1" ./configure --prefix=/usr --with-kernel=/lib/modules/2.6.20-16-generic/build --with-build=/lib/modules/2.6.20-16-generic/build --with-moddir=/lib/modules/2.6.20-16-generic/updates/alsa --with-sequencer=yes --with-isapnp=yes --with-debug=detect --with-cards="all"
checking for gcc... gcc-4.1
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc-4.1 accepts -g... yes
checking for gcc-4.1 option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc-4.1 -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc-4.1 needs -traditional... no
checking for current directory... /usr/src/modules/alsa-driver
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.20-16-generic/build
checking for directory with kernel build... /lib/modules/2.6.20-16-generic/build
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.20-16-generic
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking to modify of kernel linux/kmod.h... no
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
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.20-16-generic/updates/alsa
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... detect
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
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
checking for V4L1 layer... yes
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver version... 1.0.13
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... no
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... all
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
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
touch configure-stamp
/usr/bin/make  compile
make[2]: Entering directory `/usr/src/modules/alsa-driver'
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
cp -auvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
/usr/bin/make dep
make[3]: Entering directory `/usr/src/modules/alsa-driver'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore'
copying file alsa-kernel/core/info.c
patching file info.c
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #3 succeeded at 2815 (offset -32 lines).
Hunk #4 succeeded at 2835 (offset -32 lines).
Hunk #5 succeeded at 2888 (offset -32 lines).
Hunk #6 succeeded at 2915 (offset -32 lines).
Hunk #7 succeeded at 3006 (offset -32 lines).
Hunk #8 succeeded at 3025 (offset -32 lines).
Hunk #9 succeeded at 3044 (offset -32 lines).
Hunk #10 succeeded at 3077 (offset -32 lines).
Hunk #11 succeeded at 3110 (offset -32 lines).
Hunk #12 succeeded at 3143 (offset -32 lines).
Hunk #13 succeeded at 3172 (offset -32 lines).
Hunk #14 succeeded at 3193 (offset -32 lines).
Hunk #15 succeeded at 3211 (offset -32 lines).
Hunk #16 succeeded at 3231 (offset -32 lines).
Hunk #17 succeeded at 3243 (offset -32 lines).
Hunk #18 succeeded at 3275 (offset -32 lines).
Hunk #19 succeeded at 3341 (offset -32 lines).
Hunk #20 succeeded at 3370 with fuzz 1 (offset -32 lines).
Hunk #21 succeeded at 3411 (offset -32 lines).
Hunk #22 succeeded at 3561 (offset -32 lines).
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #2 succeeded at 1411 (offset 194 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
Hunk #1 succeeded at 309 (offset 6 lines).
copying file alsa-kernel/core/init.c
patching file init.c
Hunk #2 succeeded at 204 (offset 12 lines).
Hunk #3 succeeded at 277 (offset 13 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #1 succeeded at 1297 (offset 30 lines).
Hunk #2 succeeded at 1380 with fuzz 1 (offset 30 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #1 succeeded at 1012 with fuzz 1 (offset 17 lines).
Hunk #2 succeeded at 1925 (offset 134 lines).
Hunk #3 succeeded at 1970 with fuzz 2 (offset 125 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
Hunk #2 succeeded at 83 (offset -1 lines).
Hunk #3 succeeded at 143 (offset -1 lines).
Hunk #4 succeeded at 174 (offset -1 lines).
Hunk #5 succeeded at 207 (offset -1 lines).
Hunk #6 succeeded at 228 (offset -1 lines).
Hunk #7 succeeded at 264 (offset -1 lines).
Hunk #8 succeeded at 286 (offset -1 lines).
Hunk #9 succeeded at 311 (offset -1 lines).
Hunk #10 succeeded at 329 (offset -1 lines).
Hunk #11 succeeded at 608 (offset -1 lines).
Hunk #12 succeeded at 697 (offset -1 lines).
Hunk #13 succeeded at 712 (offset -1 lines).
Hunk #14 succeeded at 746 (offset -1 lines).
copying file alsa-kernel/core/misc.c
patching file misc.c
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
Hunk #1 succeeded at 379 with fuzz 1 (offset 2 lines).
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #1 succeeded at 2528 (offset 2 lines).
Hunk #2 succeeded at 2579 (offset 2 lines).
Hunk #3 succeeded at 2702 (offset 2 lines).
Hunk #5 succeeded at 3012 (offset -2 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
Hunk #1 succeeded at 57 (offset 6 lines).
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
Hunk #2 succeeded at 2209 (offset 68 lines).
Hunk #3 succeeded at 2558 with fuzz 1 (offset 89 lines).
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
Hunk #3 succeeded at 248 (offset 3 lines).
make[6]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[6]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
Hunk #1 succeeded at 189 (offset 3 lines).
Hunk #2 succeeded at 223 with fuzz 1 (offset 3 lines).
Hunk #3 succeeded at 326 (offset -8 lines).
make[6]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[4]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[5]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
copying file alsa-kernel/i2c/other/tea575x-tuner.c
patching file tea575x-tuner.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
Hunk #1 succeeded at 30 (offset 2 lines).
Hunk #2 succeeded at 46 (offset 2 lines).
Hunk #3 succeeded at 64 with fuzz 2 (offset 2 lines).
Hunk #4 succeeded at 92 with fuzz 2 (offset -55 lines).
Hunk #5 succeeded at 296 (offset 49 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #1 succeeded at 435 (offset 2 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[4]: Entering directory `/usr/src/modules/alsa-driver/synth'
make[5]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
Hunk #1 succeeded at 53 with fuzz 2 (offset 1 line).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #1 succeeded at 815 (offset 5 lines).
Hunk #2 succeeded at 954 (offset 6 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #1 succeeded at 41 (offset -2 lines).
Hunk #2 succeeded at 728 (offset -21 lines).
Hunk #3 succeeded at 739 (offset -21 lines).
Hunk #4 succeeded at 3052 (offset 239 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #5 succeeded at 2911 (offset 1 line).
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #1 succeeded at 35 (offset 2 lines).
Hunk #2 succeeded at 1890 with fuzz 2 (offset 77 lines).
Hunk #3 succeeded at 1924 with fuzz 2 (offset 78 lines).
copying file alsa-kernel/pci/ac97/ac97_bus.c
patching file ac97_bus.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
Hunk #1 succeeded at 262 (offset 2 lines).
Hunk #2 succeeded at 301 (offset 2 lines).
Hunk #3 succeeded at 320 (offset 2 lines).
Hunk #4 succeeded at 336 (offset 2 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/hda'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #1 succeeded at 1273 (offset 4 lines).
Hunk #2 succeeded at 2230 (offset 4 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/riptide'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[4]: Entering directory `/usr/src/modules/alsa-driver/aoa'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/core'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/core'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[6]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/aoa'
make[4]: Entering directory `/usr/src/modules/alsa-driver/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #3 succeeded at 659 (offset 1 line).
Hunk #4 succeeded at 686 (offset 1 line).
Hunk #5 succeeded at 767 (offset 1 line).
Hunk #6 succeeded at 782 (offset 1 line).
Hunk #7 succeeded at 1149 (offset 1 line).
Hunk #8 succeeded at 2073 (offset 38 lines).
Hunk #9 succeeded at 2092 (offset 38 lines).
Hunk #10 succeeded at 2109 (offset 38 lines).
Hunk #11 succeeded at 2656 (offset 45 lines).
Hunk #12 succeeded at 2728 (offset 44 lines).
Hunk #13 succeeded at 3013 (offset 44 lines).
Hunk #14 succeeded at 3085 (offset 44 lines).
Hunk #15 succeeded at 3154 (offset 44 lines).
Hunk #16 succeeded at 3172 (offset 44 lines).
Hunk #17 succeeded at 3186 (offset 44 lines).
Hunk #18 succeeded at 3199 (offset 44 lines).
Hunk #19 succeeded at 3395 (offset 70 lines).
Hunk #20 succeeded at 3486 (offset 70 lines).
Hunk #21 succeeded at 3624 (offset 76 lines).
Hunk #22 succeeded at 3645 (offset 76 lines).
Hunk #23 succeeded at 3667 (offset 76 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 225 with fuzz 2 (offset -3 lines).
Hunk #3 succeeded at 249 with fuzz 2 (offset -3 lines).
Hunk #4 succeeded at 343 (offset -3 lines).
Hunk #5 succeeded at 1363 (offset 53 lines).
Hunk #6 succeeded at 1707 (offset 58 lines).
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
Hunk #2 succeeded at 49 (offset 1 line).
Hunk #3 succeeded at 1726 (offset 27 lines).
Hunk #4 succeeded at 1775 (offset 27 lines).
Hunk #5 succeeded at 1796 (offset 27 lines).
make[5]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[3]: Leaving directory `/usr/src/modules/alsa-driver'
/usr/bin/make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/modules/alsa-driver O=/lib/modules/2.6.20-16-generic/build CPP="gcc-4.1 -E" CC="gcc-4.1" modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/hwdep.o
In file included from /usr/src/modules/alsa-driver/include/sound/driver.h:46,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of &#8216;jiffies_to_msecs&#8217;
include/linux/jiffies.h:268: error: previous definition of &#8216;jiffies_to_msecs&#8217; was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of &#8216;msecs_to_jiffies&#8217;
include/linux/jiffies.h:290: error: previous definition of &#8216;msecs_to_jiffies&#8217; was here
In file included from /usr/src/modules/alsa-driver/include/adriver.h:858,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:46,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
include/linux/pci.h:541: error: expected identifier or &#8216;(&#8217; before numeric constant
In file included from /usr/src/modules/alsa-driver/include/sound/driver.h:46,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_save_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function &#8216;pci_save_state&#8217;
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_restore_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function &#8216;pci_restore_state&#8217;
make[6]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Error 1
make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: *** [modules] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2

```

---

### Post by mlorsung on 2008-01-06
bump?  a anyone??

---

### Post by balaknair on 2008-01-09
I'm sorry to see that you still have sound issues with your sound
I've been trawling the web(other distro forums, Linux sites) to see if I could find something,  also tried to see if there was something under OSS, and found this
[http://ubuntuforums.org/showthread.php?t=601013](http://ubuntuforums.org/showthread.php?t=601013)
I think you might want to purge ALSA and reinstall it with apt-get if it doesn't work and try again, since it's probably messed up right now.
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

I guess it's also time to PM one of the more experienced members of the forum(maybe someone like LordRaiden who posted the sound guide [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449))

---

### Post by mlorsung on 2008-01-09
Balaknair,
I fixed it!  I simply reinstalled the kernel :p  I think a recent kernel upgrade broke the sound, now i need to go back through the logs and figure out which one it was...  Thanks for all of your help!
Michael

---

### Post by balaknair on 2008-01-10
Oh damn. Why didn't I think of that :mad: ](*,) ?
I had sound broken briefly when I upgraded from 2.6.20-14-generic to 2.6.20-16-generic in Gutsy, though somehow I got it working with the same steps I described above. Anyway great to hear you've got the sound issues sorted out now(don't thank me, you fixed it* in spite of* my 'help' :roll: )

PS: maybe you should mark this thread as Solved- that way others with similar problems might be able to avoid these mistakes

---

