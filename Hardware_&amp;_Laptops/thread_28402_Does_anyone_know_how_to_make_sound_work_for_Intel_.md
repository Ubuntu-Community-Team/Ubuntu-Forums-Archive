---
title: "Does anyone know how to make sound work for Intel 915GV chipset?"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by Dolboeb on 2005-04-20
Hi all,

I have a PC with Intel 915GV chipset and after installation of Hoary I found no sound device in the system. In Windows XP the device manager recognizes the built-in sound card as "Realtek High Definition Sound" and on NEC website [specification of my PC](http://www.nec-online.com.sg/Products/Product_Specs.asp?CID=2&RangeID=3&CatID=5&ModID=69) gives "Integrated High Definition Audio". I've tried to search the Net and I have only managed to find the information on Intel website about the [installation of the sound driver](http://www.intel.com/design/motherbd/av/av_drive.htm) for certain distributions, Debian/Ubuntu excluded. 

Has anyone managed to get the sound work on the same chipset? Is there any "howto" about this available? Anyone tried the instructions from Intel website?

Your help will be very appreciated!

---

### Post by devnull22 on 2005-04-20
Hello!

If the 915GV audio is anything like the intel 915GM I have on my laptop, you'll need a later version of ALSA than what is given with Ubuntu right now.

I uninstalled it and compiled alsa 1.0.9 rc2 (driver, lib, util, oss) and built them manually with support for all cards (default if you just configure with no special arguments, I only added a prefix option to configure), which is not too hard if you've ever done this (I have a slackware background, but like Kubuntu so far). After compilation and running alsaconf to let it detect the soundcard, it detected an intel high definition audio. It set the right module, which has been renamed from snd_azx to snd_hda_intel and added it to the correct config files.

Sound works for me, but is horribly scratchy... haven't got to check yet why it is so, as I'm no alsa expert. If anyone has the same problem and fixed it, I'd love some input  :wink: 

Hoping this somehow at least clarify why you don't have sound, as the snd_azx hasn't been built by default, on 2 different installs, it wasn't there anyways.

---

### Post by Dolboeb on 2005-04-20
Ok, thanks! On Intel website they also recommend to take the driver source code from them and the latest version of alsa from alsa-project.org. Maybe I'll try this one and see if I have the same problem with scratchy sound. I'll write here about the results later.

[QUOTE=devnull22]
I uninstalled it and compiled alsa 1.0.9 rc2 (driver, lib, util, oss) and built them manually with support for all cards (default if you just configure with no special arguments, I only added a prefix option to configure), which is not too hard if you've ever done this (I have a slackware background, but like Kubuntu so far). After compilation and running alsaconf to let it detect the soundcard, it detected an intel high definition audio. It set the right module, which has been renamed from snd_azx to snd_hda_intel and added it to the correct config files.

Sound works for me, but is horribly scratchy... haven't got to check yet why it is so, as I'm no alsa expert. If anyone has the same problem and fixed it, I'd love some input  :wink: 
[/QUOTE]

---

### Post by Dolboeb on 2005-04-27
I've tried to compile alsa 1.0.9rc1 but got that scratchy sound too. However, today I downloaded the lates version of alsa (rc2) and compiled it - and there's no more scratchy sound, everything works perfectly. I'll post the solution to [wiki HardwareSupportComponentsSoundCards](https://www.ubuntulinux.org/wiki/HardwareSupportComponentsSoundCards)

---

### Post by simple on 2005-05-14
bump...i get an error and have no clue about linux or kubuntu, third day on it and it's my first distro ever....
> simple@simpleb0x:~/alsa-driver-1.0.8# ./configure --with-cards=hda-intel
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
checking for current directory... /home/simple/alsa-driver-1.0.8
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)

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
checking for which soundcards to compile driver for... configure: error: Unknown soundcard hda-intel any help would rock

---

### Post by simple on 2005-05-14
i'd really love to get this going  :neutral: abotu the only thing i have left to do and i'm all setup

---

### Post by simple on 2005-05-14
](*,)

---

### Post by Dolboeb on 2005-05-15
[QUOTE=simple]bump...i get an error and have no clue about linux or kubuntu, third day on it and it's my first distro ever....
 any help would rock[/QUOTE]

Hi,

It looks like you don't have header files for your kernel...

First, I don't think it's a good idea to compile alsa 1.0.8. There may be no support for hda-intel there yet, although I'm not sure about this. But even if it does work, it will produce "scratchy" sound (see posts above). You need to download the latest development release, now it's 1.0.9rc3 I guess. I myself compiled 1.0.9rc2.

Then, you need to make sure that you have installed the following (via synaptic or apt-get):
- gcc package (3.3)
- g++ package (3.3, not sure if it's really needed though)
- linux-headers-<whatever version of kernel you're using>
For example, if you didn't change the kernel after installation of ubuntu, you need linux-headers-2.6.10-5-386 package. If you changed the kernel, then find the corresponding headers package for it in the list given by synaptic package manager (search for "headers")
-  ncurses-dev package

If you have all those packages installed as well as alsa 1.0.9 source, ./configure --with-cards=hda-intel shouldn't fail...

Hope this will help ;)
Your feedback is welcome.

Vladimir.

---

### Post by MechR on 2005-05-17
[QUOTE=Dolboeb]I've tried to compile alsa 1.0.9rc1 but got that scratchy sound too. However, today I downloaded the lates version of alsa (rc2) and compiled it - and there's no more scratchy sound, everything works perfectly. I'll post the solution to [wiki HardwareSupportComponentsSoundCards](https://www.ubuntulinux.org/wiki/HardwareSupportComponentsSoundCards)[/QUOTE]Looks like it worked for me :)  A minor nitpick about the instructions:  All the ./configure and make steps (in addition to the make install step) also need sudo to work.  Thanks \\:D/

---

### Post by Dolboeb on 2005-05-17
[QUOTE=MechR]... All the ./configure and make steps (in addition to the make install step) also need sudo to work[/QUOTE]

Hm.. why do they need sudo for them to work? I think that depends on who owns the source files and where they are. You can configure and compile it as a normal user, if all the files are downloaded and unpacked by the normal user somewhere into in the home dir (say, ~/src/alsa-<...>)...  :) 

Vladimir.

---

### Post by MechR on 2005-05-17
Hmm.  It does seem strange, but that was my experience just now.  Maybe it's just me, then... :)

---

### Post by simple on 2005-06-12
anybody get graphics working with this chipset?

---

### Post by WZot on 2005-07-29
Kinda old post to reply to..but whatever... ;)

Didnt work at all in the start..but I followed the instructions and HdaIntelSoundHowto in the Wiki. Sound appeared; but scratchy.

Installed the newest version currently available (1.0.9b). Still had the scratchy sound. But then I went to the Select Multimedia System option from the System menu and selected ESD from the top selection box. Works brilliant!

Just in case other people have the same problem...

---

### Post by WayneSchuller on 2005-09-21
[QUOTE=devnull22]Hello!
Sound works for me, but is horribly scratchy... haven't got to check yet why it is so, as I'm no alsa expert. If anyone has the same problem and fixed it, I'd love some input  :wink: 

Hoping this somehow at least clarify why you don't have sound, as the snd_azx hasn't been built by default, on 2 different installs, it wasn't there anyways.[/QUOTE]

I have found that 1.0.10rc1 has good quality sound output. The sound recording is very scratchy at this stage.

Does anyone know if this version of alsa and snd card will be automatically enabled in breezy?

---

### Post by WayneSchuller on 2005-10-28
[QUOTE=WayneSchuller]
Does anyone know if this version of alsa and snd card will be automatically enabled in breezy?[/QUOTE]

I'll answer my own question: YES!

---

