---
title: "How to listen music with headphones in ubuntu."
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by the_analyzer on 2007-10-15
My speakers are fine but my headphones dont work. How to resolve?  Any idea?

---

### Post by erginemr on 2007-10-15
Hmm, very strange. 

I can listen to music fine with my headphone, by inserting its jack to the corresponding slot on the speaker. Yours should run fine as well, unless it is some special piece of equipment that requires some driver to run.

---

### Post by the_analyzer on 2007-10-15
Yes, I said that. I dont know why. 
Note: I have an acer laptop. It reads extensa 5210.

---

### Post by Nighto on 2007-10-15
I have the same problem, with an Acer TravelMate 2480.

here is my related lspci -vv:
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0

```

---

### Post by erginemr on 2007-10-16
This may sound trivial and you may already have checked it, but there is also a "headphone" section in the sound volume settings manager (when you double click the speakers icon on your panel) 

Chances are that playing with its min/max level can help...

---

### Post by the_analyzer on 2007-10-16
> **erginemr said:**
> This may sound trivial and you may already have checked it, but there is also a "headphone" section in the sound volume settings manager (when you double click the speakers icon on your panel) 

Chances are that playing with its min/max level can help...

I didnt saw a headphones section, where it is?

I doubleclicked it and has two controls MASTER and PCM.
but there is no headphone

---

### Post by Nighto on 2007-10-16
Currently my alsamixer looks like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=46503&stc=1&d=1192544765[/IMG]

As you can see, the "headphone" switch is activated, but even so no sound comes out.

Any help is welcome... :confused:

---

### Post by erginemr on 2007-10-16
Well, the "headphones" section is not shown by default but is hidden inside the menu. Look for something like "Settings" in the menu of the gnome mixer dialog. Then you activate the "headphone" volume sliders by by selecting its checkbox in this "settings" submenu.

Not quite sure whether this will work or not (I hope so), but it is worth a try anyway (esp. if there is a dedicated headphone input slot on your laptop apart from a speaker slot, and Gnome somehow understands this.)

---

### Post by the_analyzer on 2007-10-16
HIDDEN??? where is this, I cannot find it, and that picture below, how nighto did?. I write alsamixer and shows just two "charts" I dont know where is that headphones, can anyone tell me please? 
thnx

---

### Post by erginemr on 2007-10-17
Mmm, please have a look at the following screenshots (Sorry, my mother tongue is not English)
There, you select "Settings" from the menu and check the "Headphones" option to show up the volume level.

---

### Post by erginemr on 2007-10-17
P.S. Settings show up as "Duzen" in the screenshot taken my lang. settings.

---

### Post by the_analyzer on 2007-10-17
look my snapshot, there is no settings there. we dont have the same I think.

---

### Post by Nighto on 2007-10-17
> **the_analyzer said:**
> HIDDEN??? where is this, I cannot find it, and that picture below, how nighto did?. I write alsamixer and shows just two "charts" I dont know where is that headphones, can anyone tell me please? 
thnx
apparently our soundcards are different.

tell us which soundcard you have with the following command (inside of a terminal):

lspci | grep Audio

---

### Post by erginemr on 2007-10-17
Bump!

Apparently, you have an Intel HDA sound card. Luckily, there is another ongoing thread in ubuntuforums.org regarding the same problem. Apparently, the people over there have found the solution to your problem. Please check it out:

[http://ubuntuforums.org/showthread.php?t=76307](http://ubuntuforums.org/showthread.php?t=76307)

---

### Post by erginemr on 2007-10-17
> **kbuel said:**
> Hey all,

This is what I did:

I downloaded the file that psp posted, which is [here:]("http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True")

The file should be:
realtek-linux-audiopack-3.5-2.tar.bz2

Extract it
tar xvf realtek-linux-audiopack-3.5-2.tar.bz2

Go into the directory it created and untar the file named: alsa-driver-1.0.9b_22.tar.bz2
tar xvf alsa-driver-1.0.9b_22.tar.bz2


Compile and Install:
before you do this you may need to do an sudo apt-get install build-essential
You WILL need your Linux kernel headers also, you can get these from the package manager also. 

Look for:
linux-headers-2.6.12-10
linux-headers-2.6.12-10-386

linux-headers-2.6.12-10 is the newest version.. and is probably the version you have (if you've been doing the automatic updates).  Base breezy install had linux 2.6.12-9, but there was an update to 2.6.12-10.  Basically get the version you have because it will compile it as a module for that kernel.  I think there is a way to specify what version when doing the configure, but i'm not sure how, so to get it to work for the version i'm using I removed the linux-headers-2.6.12-9, so I just had version linux-headers-2.6.12-10.


1) cd alsa-driver-1.0.9b_22
2) ./configure
3) sudo make
4) sudo make install
5) sudo ./snddevices

Then I updated a few files:
I may have updated more files then needed.... but the documentation was vague and so I put the following in a more files than were probably needed....

options snd-hda-intel model=z71v position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

I put the above lines in the BOTTOM of the following files:
/etc/modutils/alsa-base
/etc/modprobe.d/alsa-base
/etc/modprobe.d/aliases
/etc/modprobe.d/sound

(I believe I created the file /etc/modprobe.d/sound)

Again, those lines may not need to go into all those file, but that is what I did, and it worked.

I also added the following lines to the bottom of /etc/modules
snd-hda-intel
snd-ALC880

Restart the computer and then it should work.  There should be a new slider for Headphone in the volume control (next to PCM).  By default it will be muted, so unmute it before trying anything.


Lemme know if you have anymore questions.
-kbuel

Here is the killer post from that page that presumably resolved the issue and brought back the "headphone" sliders.

---

### Post by erginemr on 2007-10-17
> **W3ird_N3rd said:**
> Hey Simple, I tried zolero's tip because I felt there shouldn't be any need to compile anything.

[http://www.ubuntuforums.org/showthread.php?t=168793](http://www.ubuntuforums.org/showthread.php?t=168793)

This was it:
Quote:
With Dapper all hardwares works (almost) perfectly. Only the SPDIF OUT must be configured for listen music on headphones. For do this U need to insert this line at the bottom of file /etc/modprobe.d/alsa-base, and then make a restart

options snd-hda-intel model=z71v position_fix=1

It worked and I run 6.06 (Dapper) on an Asus A6Va :). Now listening!

Also you may try this tip from the same thread...

---

### Post by the_analyzer on 2007-10-18
yes, first, that was old,than I dont know how to compile the drivers. There were not step by step explanation. And Im a beginner. 
How can I compile those?
thnx

---

### Post by the_analyzer on 2007-10-18
I wirte ./install to install it in an automatic way.
but after I restarted the pc, nothing changed. I think in the end of the instalation it said somthing like NO ALSACONF or smth like that.

---

### Post by erginemr on 2007-10-18
Did you try adding 
options snd-hda-intel model=z71v position_fix=1
to your "/etc/modprobe.d/alsa-base" file?

Maybe that will do the trick without compling the new alsa audio driver...

---

### Post by Nighto on 2007-10-18
> **erginemr said:**
> Did you try adding 
options snd-hda-intel model=z71v position_fix=1
to your "/etc/modprobe.d/alsa-base" file?

Maybe that will do the trick without compling the new alsa audio driver...

Originally, my "/etc/modprob.d/alsabase" was like this:

```

options snd-hda-intel model=acer

```

When I tried:
```

options snd-hda-intel model=z71v position_fix=1

```
my "Surround" bar (which is like "front" here, don't know why) wasn't present, so there was no sound. I've also tried

```

options snd-hda-intel model=acer position_fix=1

```
and it reverted back (with the surround channel muted), but the headphone jack also didn't work.


Months ago, back in Feisty, i tried those Realtek driver without luck. In Feisty, i've compiled alsa-driver 1.0.15-rc1 and the headphone jack started working sometimes, and sometimes (when it was working) when i removed the headphone plug and plug it again, it stop working.

I'm trying to compile 1.0.15 final without success. Can you check what am I doing wrong?

Configure:

```

nighto@acerola:~/src/alsa-driver-1.0.15$ ./configure --with-cards=usb-audio,hda-intel --with-card-options=hda-codec-realtek --with-kernel=/usr/src/linux-source-2.6.22
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
checking for current directory... /home/nighto/src/alsa-driver-1.0.15
checking cross compile... 
checking for directory with kernel source... /usr/src/linux-source-2.6.22
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.22.9
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
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
checking for kernel linux/latency.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.22.9/misc
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
checking for driver version... 1.0.15
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... yes
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... yes
checking for nested class_device... yes
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for PnP suspend/resume... yes
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... usb-audio hda-intel
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
nighto@acerola:~/src/alsa-driver-1.0.15$ 
nighto@acerola:~/src/alsa-driver-1.0.15$ 
nighto@acerola:~/src/alsa-driver-1.0.15$ 
nighto@acerola:~/src/alsa-driver-1.0.15$ 

```

Make:

```

nighto@acerola:~/src/alsa-driver-1.0.15$ make
make dep
make[1]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15'
make[2]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #8 succeeded at 535 with fuzz 2.
copying file alsa-kernel/core/pcm.c
patching file pcm.c
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #5 succeeded at 2842 (offset 6 lines).
Hunk #6 succeeded at 2862 (offset 6 lines).
Hunk #7 succeeded at 2892 (offset 6 lines).
Hunk #8 succeeded at 2919 (offset 6 lines).
Hunk #9 succeeded at 2935 (offset 6 lines).
Hunk #10 succeeded at 2965 (offset 6 lines).
Hunk #11 succeeded at 3051 (offset 6 lines).
Hunk #12 succeeded at 3070 (offset 6 lines).
Hunk #13 succeeded at 3089 (offset 6 lines).
Hunk #14 succeeded at 3122 (offset 6 lines).
Hunk #15 succeeded at 3155 (offset 6 lines).
Hunk #16 succeeded at 3188 (offset 6 lines).
Hunk #17 succeeded at 3217 (offset 6 lines).
Hunk #18 succeeded at 3238 (offset 6 lines).
Hunk #19 succeeded at 3256 (offset 6 lines).
Hunk #20 succeeded at 3276 (offset 6 lines).
Hunk #21 succeeded at 3288 (offset 6 lines).
Hunk #22 succeeded at 3320 (offset 6 lines).
Hunk #23 succeeded at 3386 (offset 6 lines).
Hunk #24 succeeded at 3415 (offset 6 lines).
Hunk #25 succeeded at 3456 (offset 6 lines).
Hunk #26 succeeded at 3606 (offset 6 lines).
copying file alsa-kernel/core/control.c
patching file control.c
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/init.c
patching file init.c
Hunk #2 succeeded at 228 (offset 5 lines).
Hunk #3 succeeded at 254 with fuzz 2 (offset 5 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #2 succeeded at 1289 (offset -1 lines).
Hunk #3 succeeded at 1373 (offset -1 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #3 succeeded at 1904 (offset 9 lines).
Hunk #4 succeeded at 1949 (offset 9 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
Hunk #12 succeeded at 714 (offset -1 lines).
Hunk #13 succeeded at 724 (offset -1 lines).
Hunk #14 succeeded at 758 (offset -1 lines).
copying file alsa-kernel/core/misc.c
patching file misc.c
Hunk #2 succeeded at 30 (offset -1 lines).
Hunk #3 succeeded at 96 (offset -1 lines).
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/acore/ioctl32'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/acore/ioctl32'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #2 succeeded at 2590 (offset 33 lines).
Hunk #3 succeeded at 2641 (offset 33 lines).
Hunk #4 succeeded at 2764 (offset 33 lines).
Hunk #5 succeeded at 2947 (offset 33 lines).
Hunk #6 succeeded at 3074 (offset 33 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/acore/oss'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
Hunk #1 succeeded at 57 (offset 6 lines).
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
Hunk #3 succeeded at 248 (offset 3 lines).
make[4]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/acore/seq/instr'
make[4]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/acore/seq/instr'
make[4]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
make[4]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/acore/seq/oss'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/acore/seq'
make[2]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/acore'
make[2]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/i2c'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/i2c/l3'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/i2c/l3'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/i2c/other'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/i2c/other'
make[2]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/i2c'
make[2]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/drivers'
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
Hunk #1 succeeded at 830 (offset -8 lines).
Hunk #2 succeeded at 1085 (offset -8 lines).
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/drivers/mpu401'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #1 succeeded at 435 (offset 2 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/drivers/opl3'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/drivers/opl4'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/drivers/opl4'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/drivers/pcsp'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/drivers/pcsp'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/drivers/vx'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/drivers/vx'
make[2]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/drivers'
make[2]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/isa'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/isa/ad1816a'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/isa/ad1816a'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/isa/ad1848'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/isa/ad1848'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/isa/cs423x'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/isa/cs423x'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/isa/es1688'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/isa/es1688'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/isa/gus'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/isa/gus'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/isa/msnd'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/isa/msnd'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/isa/opti9xx'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/isa/opti9xx'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
Hunk #1 succeeded at 730 (offset 7 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/isa/sb'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
copying file alsa-kernel/isa/wavefront/wavefront_synth.c
patching file wavefront_synth.c
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/isa/wavefront'
make[2]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/isa'
make[2]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/synth'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/synth/emux'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/synth/emux'
make[2]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/synth'
make[2]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
Hunk #1 succeeded at 53 with fuzz 2 (offset 1 line).
copying file alsa-kernel/pci/atiixp.c
patching file atiixp.c
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #1 succeeded at 847 (offset 10 lines).
Hunk #2 succeeded at 1001 (offset 10 lines).
copying file alsa-kernel/pci/cmipci.c
patching file cmipci.c
Hunk #1 succeeded at 3072 (offset 137 lines).
Hunk #2 succeeded at 3367 (offset 149 lines).
copying file alsa-kernel/pci/ens1370.c
patching file ens1370.c
Hunk #1 succeeded at 2118 (offset -32 lines).
Hunk #2 succeeded at 2494 (offset -32 lines).
copying file alsa-kernel/pci/fm801.c
patching file fm801.c
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #2 succeeded at 704 (offset 3 lines).
Hunk #3 succeeded at 715 (offset 3 lines).
Hunk #4 succeeded at 3094 (offset 83 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #1 succeeded at 2748 (offset 2 lines).
Hunk #2 succeeded at 2934 (offset 2 lines).
copying file alsa-kernel/pci/via82xx.c
patching file via82xx.c
Hunk #1 succeeded at 2427 (offset -7 lines).
Hunk #2 succeeded at 2437 (offset -7 lines).
Hunk #3 succeeded at 2452 (offset -7 lines).
Hunk #4 succeeded at 2463 (offset -7 lines).
Hunk #5 succeeded at 2474 (offset -7 lines).
Hunk #6 succeeded at 2557 (offset -7 lines).
copying file alsa-kernel/pci/via82xx_modem.c
patching file via82xx_modem.c
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #2 succeeded at 1911 (offset 7 lines).
Hunk #3 succeeded at 1923 (offset 7 lines).
Hunk #4 succeeded at 1947 (offset 7 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/ac97'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/ali5451'
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c
Hunk #1 succeeded at 2209 (offset -8 lines).
Hunk #2 succeeded at 2379 (offset -8 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/ali5451'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/asihpi'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/asihpi'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/au88x0'
copying file alsa-kernel/pci/au88x0/au88x0.c
patching file au88x0.c
Hunk #2 succeeded at 342 (offset 1 line).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/au88x0'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/ca0106'
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c
Hunk #1 succeeded at 169 (offset 4 lines).
Hunk #2 succeeded at 1361 (offset 44 lines).
Hunk #3 succeeded at 1730 (offset 49 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/ca0106'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/cmi8788'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/cmi8788'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/cs46xx'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/cs46xx'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/cs5535audio'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/cs5535audio'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1897 (offset -29 lines).
Hunk #2 succeeded at 1960 (offset -29 lines).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
Hunk #2 succeeded at 107 (offset 2 lines).
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
Hunk #2 succeeded at 114 (offset 2 lines).
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
Hunk #2 succeeded at 128 (offset 4 lines).
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
Hunk #2 succeeded at 111 (offset 2 lines).
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
Hunk #2 succeeded at 135 (offset 6 lines).
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
Hunk #2 succeeded at 113 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
Hunk #2 succeeded at 113 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
Hunk #2 succeeded at 114 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
Hunk #2 succeeded at 121 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
Hunk #2 succeeded at 133 (offset 6 lines).
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
Hunk #2 succeeded at 126 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
Hunk #2 succeeded at 144 (offset 9 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/echoaudio'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
copying file alsa-kernel/pci/emu10k1/emu10k1x.c
patching file emu10k1x.c
Hunk #2 succeeded at 1628 (offset -7 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/emu10k1'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
Hunk #2 succeeded at 278 (offset 21 lines).
Hunk #3 succeeded at 316 (offset 21 lines).
Hunk #4 succeeded at 331 (offset 21 lines).
Hunk #5 succeeded at 347 (offset 21 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/hda'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/ice1712'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/ice1712'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #1 succeeded at 2342 (offset -1 lines).
Hunk #2 succeeded at 2503 (offset -1 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/korg1212'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/mixart'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/mixart'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/nm256'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/nm256'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/pcxhr'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/pcxhr'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/pdplus'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/pdplus'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #1 succeeded at 1279 (offset 10 lines).
Hunk #2 succeeded at 2236 (offset 10 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/riptide'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/rme9652'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/rme9652'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/trident'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/trident'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/vx222'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/vx222'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
Hunk #2 succeeded at 2045 (offset -8 lines).
Hunk #3 succeeded at 2067 (offset -8 lines).
Hunk #4 succeeded at 2407 (offset -8 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci/ymfpci'
make[2]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pci'
make[2]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/aoa'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/aoa/codecs'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/aoa/codecs'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/aoa/core'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/aoa/core'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/aoa/fabrics'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/aoa/fabrics'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/aoa/soundbus'
make[4]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/aoa/soundbus/i2sbus'
make[4]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/aoa/soundbus/i2sbus'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/aoa/soundbus'
make[2]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/aoa'
make[2]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/soc'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/soc/at91'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/soc/at91'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/soc/codecs'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/soc/codecs'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/soc/pxa'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/soc/pxa'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/soc/s3c24xx'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/soc/s3c24xx'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/soc/sh'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/soc/sh'
make[2]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/soc'
make[2]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #3 succeeded at 659 with fuzz 2 (offset -10 lines).
Hunk #4 succeeded at 686 with fuzz 2 (offset -10 lines).
Hunk #5 succeeded at 767 (offset -10 lines).
Hunk #6 succeeded at 782 (offset -10 lines).
Hunk #7 succeeded at 1160 (offset -10 lines).
Hunk #8 succeeded at 2082 (offset 3 lines).
Hunk #9 succeeded at 2101 (offset 3 lines).
Hunk #10 succeeded at 2118 (offset 3 lines).
Hunk #11 succeeded at 2675 (offset 13 lines).
Hunk #12 succeeded at 2747 (offset 13 lines).
Hunk #13 succeeded at 3035 (offset 17 lines).
Hunk #14 succeeded at 3106 (offset 17 lines).
Hunk #15 succeeded at 3227 (offset 69 lines).
Hunk #16 succeeded at 3245 (offset 69 lines).
Hunk #17 succeeded at 3259 (offset 69 lines).
Hunk #18 succeeded at 3272 (offset 69 lines).
Hunk #19 succeeded at 3476 (offset 77 lines).
Hunk #20 succeeded at 3569 (offset 79 lines).
Hunk #21 succeeded at 3706 (offset 78 lines).
Hunk #22 succeeded at 3727 (offset 78 lines).
Hunk #23 succeeded at 3748 (offset 78 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 226 (offset 1 line).
Hunk #3 succeeded at 250 (offset 1 line).
Hunk #4 succeeded at 343 (offset 1 line).
Hunk #5 succeeded at 1450 (offset 88 lines).
Hunk #6 succeeded at 1798 (offset 92 lines).
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
Hunk #3 succeeded at 1725 (offset -1 lines).
Hunk #4 succeeded at 1774 (offset -1 lines).
Hunk #5 succeeded at 1795 (offset -1 lines).
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/usb/caiaq'
copying file alsa-kernel/usb/caiaq/caiaq-audio.c
patching file caiaq-audio.c
copying file alsa-kernel/usb/caiaq/caiaq-device.c
patching file caiaq-device.c
Hunk #1 succeeded at 106 (offset 6 lines).
Hunk #2 succeeded at 313 (offset 14 lines).
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/usb/caiaq'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
Hunk #3 succeeded at 63 with fuzz 2.
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #10 succeeded at 1057 (offset -1 lines).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/usb/usx2y'
make[2]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/usb'
make[2]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pcmcia'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pcmcia/pdaudiocf'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pcmcia/pdaudiocf'
make[3]: Entrando no diretório `/home/nighto/src/alsa-driver-1.0.15/pcmcia/vx'
make[3]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pcmcia/vx'
make[2]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15/pcmcia'
make[1]: Saindo do diretório `/home/nighto/src/alsa-driver-1.0.15'
make -C /usr/src/linux-source-2.6.22 SUBDIRS=/home/nighto/src/alsa-driver-1.0.15  CPP="gcc -E" CC="gcc" modules
make[1]: Entrando no diretório `/usr/src/linux-source-2.6.22'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.22/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/nighto/src/alsa-driver-1.0.15/acore/hwdep.o
/bin/sh: scripts/genksyms/genksyms: not found
make[3]: ** [/home/nighto/src/alsa-driver-1.0.15/acore/hwdep.o] Erro 127
make[2]: ** [/home/nighto/src/alsa-driver-1.0.15/acore] Erro 2
make[1]: ** [_module_/home/nighto/src/alsa-driver-1.0.15] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-source-2.6.22'
make: ** [compile] Erro 2

```

---

### Post by erginemr on 2007-10-18
Can you please follow this thread:
[http://mrtrick.org/](http://mrtrick.org/)

Perhaps, if you follow the same steps, you may succeed. Also by the end of the article,
there is "model=auto", which is maybe worth a try.

---

