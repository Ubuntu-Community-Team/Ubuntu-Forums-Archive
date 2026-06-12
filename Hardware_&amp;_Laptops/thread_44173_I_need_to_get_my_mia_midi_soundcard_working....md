---
title: "I need to get my mia midi soundcard working..."
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by jxn on 2005-06-24
I need some help getting my mia midi soundcard working in ubuntu... alsa-project.org reports that the echo mia does have a driver named snd-mia, but I cannot modprobe it.  How can I add it so I can support my soundcard?

---

### Post by ametade on 2005-06-24
I have a echo mia (no midi) working.

> alsa-project.org reports that the echo mia does have a driver named snd-mia, but I cannot modprobe it

You cannot modprobe snd-mia because the alsa version included in Ubuntu's kernel doesn't include echo sound cards driver.

The instructions to install the driver should be at [http://xoomer.virgilio.it/g_pochini/ea.html](http://xoomer.virgilio.it/g_pochini/ea.html), but the site isn't working. You can check the [Google cache](http://216.239.59.104/search?q=cache:YjuT-VjEsOoJ:space.virgilio.it/g_pochini%40virgilio.it/ea.html+&hl=en&client=firefox).

Anyway, to install the driver follow these instructions that worked for me:

1) Download the needed alsa packages:
```

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.8.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.8.tar.bz2
wget ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.8.tar.bz2

tar -xjvf alsa-driver-1.0.8.tar.bz2
tar -xjvf alsa-firmware-1.0.8.tar.bz2
tar -xjvf alsa-tools-1.0.8.tar.bz2

```

2) Compile and install echo mia driver
```

cd alsa-driver-1.0.8
./configure --with-cards=mia
make
sudo make install

```

3) Compile and install echo mia firmware
```

cd ../alsa-firmware/echoaudio
./configure
make
sudo install

```

4) Compile and install Echo Mixer
```

cd ../../alsa-tools-1.0.8/echomixer/
./configure
make
sudo install

```

5) Finally, load the module
```

modprobe snd-mia
sudo /etc/init.d/alsasound restart

```

Hopefully at this time everything should be working fine. Good luck! :)

---

### Post by jxn on 2005-06-25
Thanks for your help, but something's not working right...I'm getting this error when trying to run the first ./configure statement:

> 
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
checking for which soundcards to compile driver for... configure: error: Unsupported soundcard mia


---

### Post by jxn on 2005-06-25
okay, I tried to get past that error by going for the alsa-1.0.9rc4 sources for the firmware/drivers/tools, but now I'm getting an error that I need to have the kernel sources installed...well, I tried to install them by using synaptic to add the kernel-sources for 2.6.10 kernel, but that, it seemed, only downloaded the giant bz2 file to /usr/src ... so then i extracted it to /usr/src/linux, but ./configure still doesn't know where the kernel sources are!  Any help?

---

### Post by ametade on 2005-06-26
Try to copy and compile all the alsa sources to /usr/src.

---

### Post by jxn on 2005-06-27
alright, that worked...but installing the 1.0.9 alsa is a mess; it keeps demanding new dependencies; I think this is what they call dependency hell. ](*,)  ](*,)  ](*,) 

Isn't there an easier way?  I'm not having much success...
For instance, now, I apparently need to install alsa-lib-1.0.9, but it's giving me the following error during compile:
> 
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check


---

### Post by jxn on 2005-06-27
apparently g++ isn't even installed by default (why is beyond me)...and, having g++-3.** isn't the same to ubuntu as having the explicitly-denoted "g++" package installed.  I'm quite frankly a little surprised and a little disappointed that so many seemingly necessary packages aren't included.  Now I remember why I haven't touched a binary distribution in 3 years.

After compiling most everything (alsa-tools/echomixer is giving me errors I don't know what to do with, but things should still modprobe, right?).  I tried to modprobe snd-mia, and no dice.  I'm getting the same error I was getting before.

---

### Post by WMCoolmon on 2005-06-28
I'm trying to get this to work as well (Supposedly the Audigy 2 NX is fixed in ALSA 1.0.9) but there's no include/version.h in the kernel sources, apparently.

---

### Post by ametade on 2005-06-28
To successfully modprobe mia you will have first to successfully compile and install the driver and firmware. It seams that you don't have the neccessary tools installed to acomplish that task. Do the following:

```
sudo apt-get install build-essential
```

Because you are trying to compile the alsa sources at /usr/src you will have to do the following:

```

cd alsa-driver-1.0.8
sudo ./configure --with-cards=mia
sudo make
sudo make install

cd ../alsa-firmware/echoaudio
sudo ./configure
sudo make
sudo install

cd ../../alsa-tools-1.0.8/echomixer/
sudo ./configure
sudo make
sudo install

```

You can't get any errors while compiling. If you get errors the most probable cause is some package that is missing in your system that you'll have to install (most of them available from apt-get/synaptic).

---

### Post by saru on 2005-07-24
Hello,

Did the original participants in this thread ever solve their dilemma?  I'd love to throw my hat in and see if we can't solve this one.  The Fedora and Gentoo folks seem to have made it happen, but I haven't been able to adobt their solutions.


I started with:
> 
	modprobe mia
	FATAL: Module mia not found.

---
Then grepped around and tried 
> 
	modprobe snd-mia
	FATAL: Module snd_mia not found.
	FATAL: Error running install command for snd_mia

---

So, after reading that 1.0.9 was where Echo support really works ... I figured I'd recompile and give alsa a fresh start with the correct modules:
> 
	wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9b.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9b.tar.bz2)
	wget [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.9.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.9.tar.bz2)
	wget [ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.9.tar.bz2](ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.9.tar.bz2)

	tar -xjvf alsa-driver-1.0.9b.tar.bz2
	tar -xjvf alsa-firmware-1.0.9.tar.bz2
	tar -xjvf alsa-tools-1.0.9.tar.bz2

---

Now to compile the drivers:

> 	cd alsa-driver-1.0.8
	sudo ./configure --with-cards=mia

(Oops, path to kernel sources missing, despite build essential package installed)
> 
	checking for directory with kernel source... /usr/src/linux
	checking for directory with kernel build...
	checking for kernel version... The file /usr/src/linux/include/linux/version.h does   not exist.
	Please, install the package with full kernel sources for your distribution
	or use --with-kernel=dir option to specify another directory with kernel
	sources (default is /usr/src/linux).

(To correct, I searched the / to find my version.h file installed in /usr/<include/linux/>; so I ran:
> sudo ./configure --with-cards=mia --with-kernel=/usr

	> checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 3.3.5 (Debian 		1:3.3.5-8ubuntu2)

	*** NO PREDEFINED KERNEL COMPILER IS DETECTED
	*** Assuming the same compiler is used with the current system compiler.

	*** Please make sure that the same compiler version was used for building kernel.

	checking for built-in ALSA... "yes"
	configure: error: You have built-in ALSA in your kernel.

Ok, so I now I am really blocked!

Didn't even bother with:
	sudo make
	sudo make install


---

Did anyone progress farther?  Does this fill any detail in?

---

### Post by saru on 2005-07-25
Well, if anyone stumbles onto this thread:

I solved the issue by:

a.  Getting the libsnd-alsa0 library
b.  Redownloading new 1.0.9b package for alsa
c.  REinstalling build essential and linux header packages
d.  Removing a tv tuner card in the system that alsa was wanting to choose over MIA (  I will deal with that guy later).

Regards,

---

### Post by ametade on 2005-08-01
Sorry about the delay...

[QUOTE=saru]Hello,

Did the original participants in this thread ever solve their dilemma?  I'd love to throw my hat in and see if we can't solve this one.  The Fedora and Gentoo folks seem to have made it happen, but I haven't been able to adobt their solutions.
[/quote]

I've used my echo mia without problems in Suse 9.2, in Ubuntu Warty and now in Ubuntu Hoary.

All of you are getting problems installing the driver because you are trying to install it with alsa 1.0.9 sources. **Hoary's kernel uses alsa 1.0.8, not alsa 1.0.9**. To install the driver use alsa 1.0.8 sources and follow the instructions I gave at posting nº 2:

[http://www.ubuntuforums.org/showpost.php?p=227782&postcount=2](http://www.ubuntuforums.org/showpost.php?p=227782&postcount=2)

Note: Remember that you have to copy all sources (kernel, alsa, etc.) to /usr/src.

---

### Post by SpectralDesign on 2006-03-14
okay, I must be missing something here....

I've been pulling my hair out for two days trying to get ALSA to properly install a module for my Echo Mia... I've tried a million and one things, including most everything mentioned in this thread...

One thing I did that I dont see mentioned is:

mkdir /usr/include
mkdir /usr/include/linux
ln -s /usr/include/linux /usr/src/linux/include

which resolved the issues around "can't find version.h"

Just this minute I also did the:

apt-get install build-essential

which I hadn't done before.... regardless, I never get further than:
(from the alsa-driver-1.0.8 directory, running ./configure --with-cards=mia)

**checking for which soundcards to compile driver for... configure: error: Unsupported soundcard mia**

Soo.... If I just do a straight ./configure then try a make it erros out here:

[B]make[1]: Leaving directory `/usr/src/alsa08/alsa-driver-1.0.8'
make -C /usr/src/linux SUBDIRS=/usr/src/alsa08/alsa-driver-1.0.8  modules
make[1]: Entering directory `/usr/src/linux'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/usr/src/linux'
make: *** [compile] Error 2
[/B]

I'm trying to get it working under Ubunto because my wife started doing librivox.org recordings, and her headset mic sounded like a p.o.s. so I decided to dig out the old Mia, mixing deck, and a *real* mic....

Sad to say, but I got this working in Windows (we dual-boot) but I'd love to delete Windows outright, as this and Photoshop are all we use it for anymore... if I can let her use the Mia in Ubuntu I'll bite the bullet and learn Gimp :)

Anyway... my son is hounding me to let him do a recording, so (cringe) here I go off to Windows land :(

Thanks for any help!

---

### Post by theorganloft on 2008-01-03
THIS IS WHAT I GET WHEN I ATTEMPT TO COMPILE FOR THE ECHO MIA MIDI: 

oem@theorganloft2:~/alsa-driver-1.0.8$ sudo ./configure --with-cards=mia
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
checking for current directory... /home/oem/alsa-driver-1.0.8
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... 
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

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
checking for which soundcards to compile driver for... configure: error: Unsupported soundcard mia
oem@theorganloft2:~/alsa-driver-1.0.8$

---

