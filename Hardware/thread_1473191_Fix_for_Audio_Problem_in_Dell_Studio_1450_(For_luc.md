---
title: "Fix for Audio Problem in Dell Studio 1450 (For lucid lynx)"
date: 2010-05-05
forum: Hardware
---

### Post by alex_kent_18 on 2010-05-05
Hi guys,

I just installed Ubuntu 10.04 on my Dell Studio 1450. Everything is working pretty well except my sound card. However, I could manage to fix it by following steps (this fix works including the audio jacks):

1. [Click here to download Realtek driver from Realtek website]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")

2. accept Terms and Conditions and click next (it will bring you to the next page)

3. in the new page, scroll down and find **Unix (linux) title** , and there you will be able to see this info : **Description** = Linux driver (2.6), **Version** = 5.15rc1, in a table. Click one of "**GO**" links in the row of the table. It will download the driver, "LinuxPkg-5.15rc1.tar.bz2".

4. _find the driver and extract it on the file system_

5. now, _start your terminal program_ and navigate to the extracted folder 
> e.g, cd Downloads/real*/alsa-driver-1.0.xx 

6. configure:
> sudo ./configure --with-cards=hda-intel

7. make:
> sudo make

8. install:
> sudo make install

9. now you may exit from your terminal and restart your computer. when it reboot again, you will hear ubuntu's login sound as usual... 

> More information about the driver can be found in readme.txt file under extracted driver folder.

**Trouble-shooting after installation info:**
> 
If you did some updates to kernel (also when update manager did some updates to kernel), your sound may lost again but don't be panic, just follow step 6 to 9 again to regain your sound. 


Have a nice day and enjoy your ubuntu day!. :KS:guitar:

> Special thanks to this thread: **[Dell New Studio 1450 sound problem]("http://ohioloco.ubuntuforums.org/showthread.php?p=8869931")**

---

### Post by biplab on 2010-05-06
CONFIRMED..........

Thanks dude. My Dell new studio 1450 is now rocking.

---

### Post by mikesaunt on 2010-05-12
Confirmed that this worked on Alienware M11X - thanks heaps!

---

### Post by alex_kent_18 on 2010-05-13
You are welcome! :)

---

### Post by mdawgmike on 2010-05-21
--Also confirmed to work in Linux Mint 9 with a Dell Studio 1458-- (although that's not much of a shock)

Thanks!  I just got my Dell laptop and the first thing I wanted to do was load Linux.  The sound not working properly is what has hung me up and I can't even say how many different things I've tried.  This finally did it and it all works perfect.

The sad part about all this is that what I now have working in Linux is better driver support than what Dell provides for Windows 7. I'm dual-booting to a clean install of Windows 7 without all the Dell bloatware (although I kept the restore partition in-tact just in case I ever need to go back to stock), and I have yet to find drivers for my built-in wireless adapter and something that makes my 'DVD eject' key function in Windows.  Both of which surprisingly work out of the box with my distro :D.

---

### Post by black2blacky on 2010-06-23
[SIZE=2][SIZE=4][COLOR=Red]Thankx a lot alex[/COLOR][/SIZE], but the procedure didnt work for my 64 bit ubuntu, and i tried with some more commands inbetween your commands collected from diffrent forums,
that i have posted in the following link

[/SIZE]> [SIZE=2]http://ubuntuforums.org/showthread.php?p=9498759#post949875[/SIZE]9:lolflag:

---

### Post by Eugene C. on 2010-06-30
Awesome fix! It worked for me; I've got a Dell Studio 1458 running Ubuntu x64. Thanks bro ski.

---

### Post by albanprashanth on 2010-07-17
I have done what you have posted earlier but now it says "NO SOUND CARDS"

The following appears on my terminal
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
checking for current directory... /home/prashanth/Downloads/alsa-driver-1.0.23
checking cross compile... 
checking for directory with ALSA kernel sources... ../alsa-kmirror
checking for directory with kernel source... /lib/modules/2.6.32-21-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h ... linux/version.h
checking for kernel linux/autoconf.h generated/autoconf.h... linux/autoconf.h
checking for kernel linux/utsrelease.h generated/utsrelease.h... linux/utsrelease.h
checking for kernel version... 2.6.32-21-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3

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
checking for directory to store kernel modules... /lib/modules/2.6.32-21-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
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
checking for kernel linux/usb/audio-v2.h... no
Creating <linux/usb/audio-v2.h>...
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
checking for cards to compile driver for... hds-intel
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
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
prashanth@ubuntu:~/Downloads/alsa-driver-1.0.23$ sudo make
make dep
make[1]: Entering directory `/home/prashanth/Downloads/alsa-driver-1.0.23'
make[2]: Entering directory `/home/prashanth/Downloads/alsa-driver-1.0.23/include'
make -C sound prepare
make[3]: Entering directory `/home/prashanth/Downloads/alsa-driver-1.0.23/include/sound'
make prepare2
make[4]: Entering directory `/home/prashanth/Downloads/alsa-driver-1.0.23/include/sound'
ln -s ../../alsa-kernel/include/cs4231-regs.h
ln -s ../../alsa-kernel/include/cs46xx.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_scb_types.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_spos.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_task_types.h
ln -s ../../alsa-kernel/include/cs8403.h
ln -s ../../alsa-kernel/include/cs8427.h
ln -s ../../alsa-kernel/include/emu10k1.h
ln -s ../../alsa-kernel/include/emu10k1_synth.h
ln -s ../../alsa-kernel/include/emu8000.h
ln -s ../../alsa-kernel/include/emu8000_reg.h
ln -s ../../alsa-kernel/include/emux_legacy.h
ln -s ../../alsa-kernel/include/emux_synth.h
ln -s ../../alsa-kernel/include/es1688.h
ln -s ../../alsa-kernel/include/gus.h
ln -s ../../alsa-kernel/include/hda_hwdep.h
ln -s ../../alsa-kernel/include/hdsp.h
ln -s ../../alsa-kernel/include/hdspm.h
ln -s ../../alsa-kernel/include/hwdep.h
ln -s ../../alsa-kernel/include/i2c.h
ln -s ../../alsa-kernel/include/info.h
ln -s ../../alsa-kernel/include/initval.h
ln -s ../../alsa-kernel/include/jack.h
ln -s ../../alsa-kernel/include/l3.h
ln -s ../../alsa-kernel/include/memalloc.h
ln -s ../../alsa-kernel/include/minors.h
ln -s ../../alsa-kernel/include/mixer_oss.h
ln -s ../../alsa-kernel/include/mpu401.h
ln -s ../../alsa-kernel/include/opl3.h
ln -s ../../alsa-kernel/include/opl4.h
ln -s ../../alsa-kernel/include/pcm-indirect.h
cp ../../alsa-kernel/include/pcm.h .
patch -p0 -i pcm.patch pcm.h
make[4]: patch: Command not found
make[4]: *** [pcm.h] Error 127
make[4]: Leaving directory `/home/prashanth/Downloads/alsa-driver-1.0.23/include/sound'
make[3]: *** [prepare] Error 2
make[3]: Leaving directory `/home/prashanth/Downloads/alsa-driver-1.0.23/include/sound'
make[2]: *** [prepare] Error 2
make[2]: Leaving directory `/home/prashanth/Downloads/alsa-driver-1.0.23/include'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/prashanth/Downloads/alsa-driver-1.0.23'
make: *** [include/sndversions.h] Error 2
prashanth@ubuntu:~/Downloads/alsa-driver-1.0.23$ sudo make install
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /home/prashanth/Downloads/alsa-driver-1.0.23/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/prashanth/Downloads/alsa-driver-1.0.23/include'
make[1]: Nothing to be done for `modules_install'.
make[1]: Leaving directory `/home/prashanth/Downloads/alsa-driver-1.0.23/include'
make[1]: Entering directory `/home/prashanth/Downloads/alsa-driver-1.0.23/acore'
mkdir -p /lib/modules/2.6.32-21-generic/kernel/sound/acore
cp snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.32-21-generic/kernel/sound/acore
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/prashanth/Downloads/alsa-driver-1.0.23/acore'
make: *** [install-modules] Error 1



PLZ help me:oops:

---

### Post by alex_kent_18 on 2010-07-24
Hi albanprashanth,

I found that you have not installed "Patch" package yet. 

To install "Patch", 
- Please go to Synaptic Package Manager, 
- Find "Patch" from quick search, 
- and install it.

After Patch installation, please try again.

Best regards,
Alex

---

### Post by swaprava on 2010-07-24
I was using the alsamixer in ubuntu 10.04 on Dell 1435, and sound was working fine. However, just after upgrading in the last update, the sound completely stopped working. I thought first it might be a hardware issue, but junked it since sound was working perfect on the windows partition I have. For ubuntu, not a single sound is working, even the login screen sound at the boot. I followed the instructions in this post, and still it doesn't work. The Readme file in the realtek audiopack goes as:

```
The source code copy from www.alsa-project.org.      ver:5.15
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC267
ALC268
ALC259
ALC269
ALC270
ALC272
ALC273
ALC275
ALC660
ALC660VD
ALC661
ALC662
ALC663
ALC665
ALC670
ALC680
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A
ALC892

Installation:
This Source Code is from www.alsa-project.org.
For OS installation, please remember add the Development tool kit.
For driver installation, please follow below steps. 

Automatic install: (Recommend RedHat distribution)
execute

  ./install

Note: Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words.   

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Complied source code
    a. cd alsa-driver-1.0.xx
    b. ./configure --with-cards=hda-intel
    c. make
    d. make install

Step 3. reboot your machine

Step 4. Use the alsamixer the disable mute (All audio line default is mute)
        Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note:     1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
    2. Kernel Version must be 2.6 or later.
    3. All mixer channels are muted by default. You must use a native
        or OSS mixer program to unmute appropriate channels.
    4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
    5. The driver added to support the SPDIF functoin.     
    6. a. You can download the alsa-lib-1.0.x and alsa-utils-1.0.x form the www.alsa-project.org, then unzip and install them. 
       b. Suggest use "alsamixer" to control mixer function.
       c. Used "alsaconf" can autodetect which drive you need to install (step 4).     
        7. SUSE Distribution must install the ncurses package. 
```I couldn't completely understand how to disable all mute in alsamixer (step 4 above). Since typing alsamixer on the terminal gives [this]("http://www.flickr.com/photos/swaprava/4824507575/") output.

I'm not sure how to get back sound on my system. Please help. :(

---

### Post by ybbob549 on 2010-09-30
> **alex_kent_18 said:**
> Hi guys,

I just installed Ubuntu 10.04 on my Dell Studio 1450. Everything is working pretty well except my sound card. However, I could manage to fix it by following steps (this fix works including the audio jacks):

1. [Click here to download Realtek driver from Realtek website]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")

2. accept Terms and Conditions and click next (it will bring you to the next page)

3. in the new page, scroll down and find **Unix (linux) title** , and there you will be able to see this info : **Description** = Linux driver (2.6), **Version** = 5.15rc1, in a table. Click one of "**GO**" links in the row of the table. It will download the driver, "LinuxPkg-5.15rc1.tar.bz2".

4. _find the driver and extract it on the file system_

5. now, _start your terminal program_ and navigate to the extracted folder 
 

6. configure:


7. make:


8. install:


9. now you may exit from your terminal and restart your computer. when it reboot again, you will hear ubuntu's login sound as usual... 



**Trouble-shooting after installation info:**


Have a nice day and enjoy your ubuntu day!. :KS:guitar:



THANKS A LOTTTTTTTTTTTTTTTTT ..i got sound after 6months of installation:) thank u very muchhhh...Now rocking:guitar:

---

### Post by vicap on 2011-06-01
Thank you so soo much Man!! Ive been trying to fix it for a very long time but never got succeeded. 
You Rock!!
V

---

### Post by independent on 2011-11-30
:lolflag:thanx buddy............it works!!!:guitar:

---

