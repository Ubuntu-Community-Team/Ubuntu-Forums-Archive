---
title: "No sound on Sony Vaio PCG-505 CBP (Japanese model)"
date: 2005-02-04
forum: Hardware &amp; Laptops
---

### Post by brainstuff on 2005-02-04
*total linux noob alert*
Hi,
I got an old Sony Vaio I got off my neighbour last night who was about to chuck it out because he couldn't get it to start! :shock:.

It's a pretty old Pentium MMX 300Mhx 64Mb (64Mb more on the way). Very dead battery, but I got it to start up again by just plugging it in and leaving the BIOS battery to get a little charge for a few hours.

Anyway - everything seemed to install ok, but it simply didn't detect the soundcard. I know it was working under Win2K before I banished that old demon.

Sadly I don't have the lappy with me but I'll add to this post later on with an lsmod list thingy. Please bear in mind that this is my second ever Linux install...the first being 3 days ago on a Thinkpad, and everything worked for me first time!

Are there any other tips that you guys can give me to get the sound working? It's not the end of the world if it never works, cos I'm giving the machine to my Dad to use open office and write emails on, but I wanted to pre-install it with XMMS and a load of mp3s of his favourite old prog-rock bands :p

Thanks in advance
brain

---

### Post by brainstuff on 2005-02-04
Heh, I might've answered my own questions again:

From here:
[http://www.joechiu.com/computing/vaio/linuxon505.html](http://www.joechiu.com/computing/vaio/linuxon505.html)

> 
Processing digital audio with built-in sound hardware
Run sndconfig to setup SoundBlaster 16 compatible audio

As root, run the RedHat sound configuration program:

# sndconfig

sndconfig will report "No PNP/PCI Audio Detected". Continue and choose the SoundBlaster 16 setting. Set the settings as follows:


 I/O ADDR

IRQ 1

DMA

IRQ 2

MPU I/O

220

5

1

5

330

When you accept the settings and test the audio, you should hear a test message.

sndconfig will updated /etc/conf.modules so that the values will auto-load correctly in the future.


---

### Post by brainstuff on 2005-02-04
argh I don't know if it's considered poor etiquette to post three times in a row, but this is doing my head in....Ubuntu doesn't have a 'sndconfig' - at least as far as I can find...

Help!



edit:
note to self
[http://translate.google.com/translate?u=http%3A%2F%2Fwww.geocities.com%2FSiliconValley%2FProgram%2F1018%2Flinux%2Fvaio.html&langpair=ja%7Cen&hl=en&safe=off&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools](http://translate.google.com/translate?u=http%3A%2F%2Fwww.geocities.com%2FSiliconValley%2FProgram%2F1018%2Flinux%2Fvaio.html&langpair=ja%7Cen&hl=en&safe=off&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools)

---

### Post by brainstuff on 2005-02-04
right...I've tried the latest alsa driver - below are the results - I'm aiming at the generic ES18xx driver, as the japanese link above I found reckons it's the ES1879 in the vaio 505v's. I even managed to install gcc for the purposes of this exercise - but that might be part of the problem...can anyone who unlike me, knows what they're doing give me a hand? I'll buy you a virtual pint!


root@xxNAMExx:/home/xxNAMExx/alsa-driver-1.0.8 # ./configure --with-cards=es1879 --with-sequencer=yes;make;make install
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
checking for current directory... /home/xxNAMExx/alsa-driver-1.0.8
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 3.3.4 (Debian 1:3.3.4-9ubuntu5)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "no"
checking for existing ALSA module... "no"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "yes"
cat: /usr/src/linux/include/linux/kmod.h: No such file or directory
checking for kernel linux/compiler.h... "no"
checking for kernel linux/pm.h... "no"
checking for kernel linux/spinlock.h... "no"
checking for kernel linux/irq.h... "no"
checking for kernel linux/threads.h... "no"
checking for kernel linux/rwsem.h... "no"
checking for kernel linux/gameport.h... "no"
checking for kernel linux/devfs_fs_kernel.h... "no"
checking for kernel linux/highmem.h... "no"
checking for kernel linux/workqueue.h... "no"
checking for kernel linux/dma-mapping.h... "no"
checking for kernel asm/hw_irq.h... "no"
checking for kernel linux/device.h... "no"
checking for kernel linux/jiffies.h... "no"
checking for kernel linux/compat.h... "no"
checking for kernel linux/adb.h... "no"
checking for kernel linux/cuda.h... "no"
checking for kernel linux/pmu.h... "no"
checking for kernel linux/moduleparam.h... "no"
checking for kernel linux/syscalls.h... "no"
checking for kernel linux/firmware.h... "no"
checking for exported symbol dump_stack... grep: /usr/src/linux/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "no"
checking for PCI support in kernel... "no"
checking for I2C driver in kernel... unknown
checking for firmware loader... unknown
checking for SGI/MIPS (HAL2) architecture... "no"
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... "unknown"
checking for SMP... "no"
checking for ISA PnP driver in kernel... no
checking for PnP driver in kernel... no
checking for ISA PnP support... yes
checking for strlcpy... "no"
checking for snprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for pci_dev_present... "no"
checking for tty->count is the atomic type... "no"
checking for remap_pfn_range... "no"
checking for new remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for acpi_register_gsi... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
checking for driver version... 1.0.8
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for Procfs support... "no"
checking for USB support... "no"
checking for USB module support... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "no"
checking for PCMCIA module support... "no"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "no"
checking for parallel port module support... "no"
checking for which soundcards to compile driver for... configure: error: Unknown soundcard es1879
make all-deps
make[1]: Entering directory `/home/xxNAMExx/alsa-driver-1.0.8'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/xxNAMExx/alsa-driver-1.0.8'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/home/xxNAMExx/alsa-driver-1.0.8/acore'
Makefile:6: /home/xxNAMExx/alsa-driver-1.0.8/Makefile.conf: No such file or directory
make[1]: *** No rule to make target `/home/xxNAMExx/alsa-driver-1.0.8/Makefile.conf'.  Stop.
make[1]: Leaving directory `/home/xxNAMExx/alsa-driver-1.0.8/acore'
make: *** [install-modules] Error 1
root@xxNAMExx:/home/xxNAMExx/alsa-driver-1.0.8 #

---

### Post by michele on 2005-02-09
looks like alsa doesn't know the card you have selected.
The configure script fails and therefore nothing is built.

check the list
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

M

---

### Post by brainstuff on 2005-02-09
hi Michele
Thanks for the link. Due to a couple of other performance issues (would you believe Win2K runs better on that little old box :shock: ) I've ditched ubuntu on the 505 and given it to my Dad...But I've had nothing but joy from Ubuntu on my old Thinkpad...getting to the point where I'm seriously considering dual-booting one of my main PCs just to see how it runs on a **proper** machine :)

---

### Post by mikecar52 on 2005-06-01
[QUOTE=brainstuff]*total linux noob alert*
Hi,
I got an old Sony Vaio I got off my neighbour last night who was about to chuck it out because he couldn't get it to start! :shock:.

It's a pretty old Pentium MMX 300Mhx 64Mb (64Mb more on the way). Very dead battery, but I got it to start up again by just plugging it in and leaving the BIOS battery to get a little charge for a few hours.

Anyway - everything seemed to install ok, but it simply didn't detect the soundcard. I know it was working under Win2K before I banished that old demon.

Sadly I don't have the lappy with me but I'll add to this post later on with an lsmod list thingy. Please bear in mind that this is my second ever Linux install...the first being 3 days ago on a Thinkpad, and everything worked for me first time!

Are there any other tips that you guys can give me to get the sound working? It's not the end of the world if it never works, cos I'm giving the machine to my Dad to use open office and write emails on, but I wanted to pre-install it with XMMS and a load of mp3s of his favourite old prog-rock bands :p

Thanks in advance
brain[/QUOTE]
 sndconfig may help.
If not downloadable from ubuntu,
debian should have it   Install it and run, it may help you configure your card.
Also try a few different ways to get it to run in thyee control panel.
cheers

---

