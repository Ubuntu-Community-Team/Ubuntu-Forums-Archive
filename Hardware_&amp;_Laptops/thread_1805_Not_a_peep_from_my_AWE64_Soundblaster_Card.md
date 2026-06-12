---
title: "Not a peep from my AWE64 Soundblaster Card"
date: 2004-10-23
forum: Hardware &amp; Laptops
---

### Post by Acid_Wit on 2004-10-23
Not a peep from my AWE64 Soundblaster Card - any ideas - anybody?

---

### Post by im_ka on 2004-10-23
is your soundcard recognized?
is the module loaded?
have you checked the mixer settings? -> application menu/multimedia

any error messages when you try to play sound files?

---

### Post by daveiler on 2004-10-23
I have an ISA AWE64 Value I'm used to this by now

[alsa page for us](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+64+Value.&chip=sb16%2C+emu8000&module=sbawe) 

short version

sudo -s
modprobe snd-sbawe;modprobe snd-pcm-oss;
modprobe snd-mixer-oss;modprobe snd-seq-oss


use volume control to turn up :)
try it out :)

---

### Post by passdoubt on 2005-01-03
[QUOTE=daveiler]I have an ISA AWE64 Value I'm used to this by now

[alsa page for us](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+64+Value.&chip=sb16%2C+emu8000&module=sbawe) 

short version

sudo -s
modprobe snd-sbawe;modprobe snd-pcm-oss;
modprobe snd-mixer-oss;modprobe snd-seq-oss
[/QUOTE]

I am having a similar Issue with my ISA AWE64. I checked out the the alsa page  not much help im afraid  here is the output of modprobe 

$ sudo modprobe snd-sbawe
FATAL: Error inserting snd_sbawe (/lib/modules/2.6.8.1-3-686/kernel/sound/isa/sb/snd-sbawe.ko): No such device

all the other modprobe commands work and i get this when i run modinfo

$ modinfo snd-sbawe
filename:       /lib/modules/2.6.8.1-3-686/kernel/sound/isa/sb/snd-sbawe.ko
author:         Jaroslav Kysela <perex@suse.cz>
license:        GPL
description:    Sound Blaster AWE
parm:           index:Index value for SoundBlaster 16 soundcard.
parm:           id:ID string for SoundBlaster 16 soundcard.
parm:           enable:Enable SoundBlaster 16 soundcard.
parm:           isapnp:PnP detection for specified soundcard.
parm:           port:Port # for SB16 driver.
parm:           mpu_port:MPU-401 port # for SB16 driver.
parm:           fm_port:FM port # for SB16 PnP driver.
parm:           awe_port:AWE port # for SB16 PnP driver.
parm:           irq:IRQ # for SB16 driver.
parm:           dma8:8-bit DMA # for SB16 driver.
parm:           dma16:16-bit DMA # for SB16 driver.
parm:           mic_agc:Mic Auto-Gain-Control switch.
parm:           csp:ASP/CSP chip support.
parm:           seq_ports:Number of sequencer ports for WaveTable synth.
vermagic:       2.6.8.1-3-686 preempt 686 gcc-3.3
depends:        snd-sb-common,snd-opl3-lib,snd,snd-mpu401-uart,snd-sb16-dsp,snd-sb16-csp,snd-seq-device
alias:          pnp:cCTL0035dCTL0031dCTL0021*
alias:          pnp:cCTL0039dCTL0031dCTL0021*
alias:          pnp:cCTL0042dCTL0031dCTL0021*
alias:          pnp:cCTL0043dCTL0031dCTL0021*
alias:          pnp:cCTL0044dCTL0031dCTL0021*
alias:          pnp:cCTL0045dCTL0031dCTL0021*
alias:          pnp:cCTL0046dCTL0031dCTL0021*
alias:          pnp:cCTL0047dCTL0031dCTL0021*
alias:          pnp:cCTL0048dCTL0031dCTL0021*
alias:          pnp:cCTL0054dCTL0031dCTL0021*
alias:          pnp:cCTL009adCTL0041dCTL0021*
alias:          pnp:cCTL009cdCTL0041dCTL0021*
alias:          pnp:cCTL009fdCTL0041dCTL0021*
alias:          pnp:cCTL009ddCTL0042dCTL0022*
alias:          pnp:cCTL009edCTL0044dCTL0023*
alias:          pnp:cCTL00b2dCTL0044dCTL0023*
alias:          pnp:cCTL00c1dCTL0042dCTL0022*
alias:          pnp:cCTL00c3dCTL0045dCTL0022*
alias:          pnp:cCTL00c5dCTL0045dCTL0022*
alias:          pnp:cCTL00c7dCTL0045dCTL0022*
alias:          pnp:cCTL00e4dCTL0045dCTL0022*
alias:          pnp:cCTL00e9dCTL0045dCTL0022*
alias:          pnp:cCTL00eddCTL0041dCTL0070*
alias:          pnp:cCTLXXXXdCTL0031dCTL0021*
alias:          pnp:cCTLXXXXdCTL0041dCTL0021*
alias:          pnp:cCTLXXXXdCTL0042dCTL0022*
alias:          pnp:cCTLXXXXdCTL0044dCTL0023*
alias:          pnp:cCTLXXXXdCTL0045dCTL0022*
alias:          pnp:ctBA03b0dPNPb003*

this would lead me to belive that the module is installed  but the sound card isnt being detected when the kernel ( 2.6.8 ) starts.  I have been getting this error at startup am I missing something?

alsact1: load_state:1134
no sound cards found 

any help would be greatly appreciated

---

### Post by for_usenet on 2005-01-04
Not sure if this will help, but I had similar issues with an ISA Vibra 16 SoundBlaster
card.  In my case, when I tried to do:

    $ sudo modprobe sb

It would also give me the "device not found" or "no such device" message.

After googling around a little, I found a solution that works somewhat, though not
ideally.  If you give the module (in your case, sb-awe) the parameters for the card
(like irq, dma, mem, etc) then it might work.  It did for me and my Vibra card, so
it might for you.

However, I ran into another issue.  If I add this module to /etc/modules, with the
right parameters, gnome programs, or GUI programs (XMMS in particular) don't
see the card.  Running dmesg shows the card IS recognized, but nothing in the
GUI will see it.  Only after the GUI starts up, and I run the modprobe command
with the right switches, will XMMS see and use the ISA sound card.  So my qus
is:  How do I get the system to recognize the card without having to manually
probe for it ?

cheers

---

### Post by passdoubt on 2005-01-04
hey im working on you suggestion now.  what iv came across in my reading is that sb is an oss sound driver you might need to get the alsa-oss package from synaptic
I could be way off base here though

as to my probliem i tried again to compile the new drivers from alsa and it gives me an error message saying sound card not supported im not sure how that can be, but an interesting note as it was compiling it goes through the list of kernel options and ISA PnP is not in my kernel.  Do other ubuntu users with isa sound cards have this installed?

---

### Post by for_usenet on 2005-01-05
I'm not sure what additional packages you might need.  But I can tell you what I have
and works.  First off, in /boot/config-2.6.8.1-3-386, the various (seemingly relevant)
kernel config options, with line numbers, are:

    7     CONFIG_GENERIC_ISA_DMA=y
    205   CONFIG_ISA=y
    206   CONFIG_EISA=y    (there are a bunch of other ISA/EISA options around
here that are also enabled)
    396   CONFIG_ISAPNP=y    (and two others below this which are also =y)
    2217  CONFIG_SND_OSSEMUL=y (this is under the ALSA section in the kernel)
    2257  CONFIG_SND_SB8=m
    2258  CONFIG_SND_SB16=m
    2259  CONFIG_SND_SBAWE=m

The option on line 2217 is why I made the statement that I'm not sure if you need
any other specific software.  Running dpkg -l | grep alsa gives me alsa-base and
alsa-utils as installed.

All these files are from a 4.10 Warty installation.  I have not added any packages or
software outside of Ubuntu's .deb repository.  I've edited a couple of system files, but
not the ones mentioned here, so my line numbers should be accurate.  My apologies
if they are not.  Hope this gives you a more definitive idea of what might or might not
be enabled.

For the record, the line I had to add to /etc/modules so that my ISA Vibra 16 card is
recognized is:

    sb io=0x220 irq=5 dma=1 dma16=3

Not sure what they should be for your AWE, but googling might turn something up.

cheers

---

### Post by sputnik on 2005-01-10
This has been my problem too, including the problem with modprobe.

I've used isapnptools to generate an isapnp.conf file

 pnpdump > /etc/isapnp.conf.  (I found the instructions at [http://www.linuxselfhelp.com/HOWTO/mini/Soundblaster-AWE.html](http://www.linuxselfhelp.com/HOWTO/mini/Soundblaster-AWE.html) this assumes an older kernel, and talks about recompiling the kernel for sound support - I haven't done this - yet ;-) )
I've then uncommented what I hope are the relevant lines of this file (there is a degree of multiple choice), having messed around slightly with IRQ and memory conflicts - (it does not seem to use the same IRQ setting as it did under Windoze).
However, during bootup I can see that the machine at least acknowledges the presence of my card.
modprobe snd-sbawe no longer produces any fatal errors - but still no sound.

---

### Post by sputnik on 2005-01-10
ps 
I have tried
# modinfo soundcore
and get the following:-
filename:       /lib/modules/2.6.8.1-4-686/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.8.1-4-686 preempt 686 gcc-3.3
depends:

I assume this means no kernel recompilation is necessary

---

### Post by sputnik on 2005-01-10
Forgot to add this
typing
/sbin/isapnp /etc/isapnp.conf
gives this result (use sudo if not root terminal)

Board 1 has Identity 10 1d 31 4d 7a c5 00 8c 0e:  CTL00c5 Serial No 489770362 [checksum 10]
CTL00c5/489770362[0]{Audio               }: Ports 0x220 0x330 0x388; IRQ5 DMA1 DMA5 --- Enabled OK
CTL00c5/489770362[2]{WaveTable           }: Port 0x620; --- Enabled OK

---

### Post by for_usenet on 2005-01-10
So if you look through /lib/modules/2.6.8.1-4-686/kernel/ and its subdirectories, you
should find a module named snd-sbawe.ko, or something similar.  Then, if you modprobe
this module with the parameters you got, it might just work ;-)  i.e.

    $ sudo modprobe snd-sbawe io=0x220 irq=5 dma=1 dma16=5

and you should get sound.  If that still doesn't work, check this link out:

    [http://ubuntuguide.org/#sorrynomixer](http://ubuntuguide.org/#sorrynomixer)

cheers

---

### Post by sputnik on 2005-01-11
Getting better!   :-)
When I do this I can at least get the mixer application to come up. :-k 
No sound when I play a CD.  Does it matter that I have both Alsa and OSS tabs coming up on the  Volume control?
Presumably I need to add snd-sbawe etc to /etc/modules

What about the
[list]
[*]snd-pcm-oss
[*]snd-pcm-oss;
snd-mixer-oss 
[*]snd-seq-oss
[/list] 
These too?  Do I need to do anything with alsactl?

---

### Post by for_usenet on 2005-01-11
Cool.  To /etc/modules, add a line with snd-sbawe and with the parameters listed in my previous message (i.e. same line, just without the sudo modprobe).

I don't remember having to do anything with alsactl.  After running the command from the "nomixer" error, I was able to use the volume controls on the mixer, and even on the menubar on the screen, which I couldn't before.  Another command that might be helpful is dmesg | grep sbawe, which parses the kernel message log for any events involving the sbawe module.

As for the other modules, I seem to remember that if I did a modprobe on a module, it would load the other modules needed to run.  I must admit that I no longer have the Ubuntu machine I set up - I had to return it to the people I was setting it up for...

cheers

---

### Post by sputnik on 2005-01-12
Don't know what was happening last night but it all works on boot-up this evening :D 
I have added those options to /etc/modules
I can now play CDs :cool:, 
My daughter will be able to access CBeebies with sound - so teletubbies and tweenies with sound - :o 

I also found this reference do setting this up with an earlier kernel in Debian
[http://www.tux.org/~tbr/sound-debian/](http://www.tux.org/~tbr/sound-debian/) which may be of some help to someone.
It talks about using modules sb, awe_wave, and opl3 - I'm assuming this is all covered by snd-sbawe. but I'll probably come back to it a later date now this is working adequately.

---

### Post by brousch on 2005-02-04
I have been trying to get my SB16 ISA card to work for a while. This is what finally worked for me last night:

In  */etc/modules* I added the line:
sb io=0x220 irq=5 dma=1 dma16=3

I then reinstalled all relevant alsa, oss, alsa-oss, and sound packages through Synaptic.

The sound came right up when I rebooted.

I would like to thank For_Usenet for the solution that finally worked for me!

---

### Post by Tiede on 2005-02-07
[QUOTE=daveiler]I have an ISA AWE64 Value I'm used to this by now

[alsa page for us](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+64+Value.&chip=sb16%2C+emu8000&module=sbawe) 

short version

sudo -s
modprobe snd-sbawe;modprobe snd-pcm-oss;
modprobe snd-mixer-oss;modprobe snd-seq-oss


use volume control to turn up :)
try it out :)[/QUOTE]

When I try those, all but one work: modprobe snd-seq-oss
It reads:
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.8.1-3-386/kernel/sound/core/seq/oss/snd-seq-oss.ko): Device or resource busy

What should I do :(


EDIT: Just want to add that if  I dmesg, it says the card is there...
Relevant lines:

isapnp: Scanning for PnP cards...
pnp: SB audio device quirk - increasing port range
pnp: AWE32 quirk - adding two ports
isapnp: Card 'Creative SB AWE64 PnP'
isapnp: 1 Plug & Play card detected total

I am running out of ideas, here. If you can help, don't hesitate!

---

### Post by Tiede on 2005-02-09
[QUOTE=brousch]I have been trying to get my SB16 ISA card to work for a while. This is what finally worked for me last night:

In  */etc/modules* I added the line:
sb io=0x220 irq=5 dma=1 dma16=3

I then reinstalled all relevant alsa, oss, alsa-oss, and sound packages through Synaptic.

The sound came right up when I rebooted.

I would like to thank For_Usenet for the solution that finally worked for me![/QUOTE]
 Just want to say that when I add the line
sb io=0x220 irq=5 dma=1 dma16=3
to /etc/modules and restart the system,
Warty report that it failed to find device 01:00:00 (or something like that, I don't remember the exact line, sorry) and then just hangs there. I then have to manually restart and go to a shell and edit that line out of the /etc/modules file...

If someone knows why,...

---

### Post by Tiede on 2005-02-14
OK I did a fresh install and I still don't have sound. (at least now I here the default beep sound, before I couldn't).
Well, since the options on top didn't worl for me so far, I did not even bother with them on muy new install. Except gst-register-0.8 wich loaded very well.

I stumble upon [ this page ](http://www.alsa-project.org/~iwai/awedrv-faq.html#Q2.1) and tried it. But for a reason, It stops at the install like so:
```

marc@Linuxed:~/awedrv-0.4.4 $ sh ./install.sh
Linux source root directory [/usr/src/linux]
entry /usr/src/linux already exists: input again.

Linux source root directory [/usr/src/linux] ifiputsomethingelse
entry ifiputsomethingelse already exists: input again.

```

Does anyone know what I should do next. How can I make it work. I really thought this was it.

Thanks for your help so far...

---

### Post by Tiede on 2005-02-26
Ok. I figured out what seemed to be the prob. The linux folder is in /usr/**include**/linux, not /usr/*src*/linux....

when I properly insert it, this is what happens:

```

root@Linuxed:/home/marc/awedrv-0.4.4 # sh ./install.sh
Linux source root directory [/usr/src/linux] /usr/include/linux
making symlink /usr/include/linux/include/asm
make: *** Pas de règle pour fabriquer la cible « symlinks ». Arrêt.
checking the version of installed sound driver..
./install.sh: line 44: cc: command not found
./install.sh: line 1: /tmp/getver7802: Aucun fichier ou répertoire de ce type
Unknown sound driver version. quit.
root@Linuxed:/home/marc/awedrv-0.4.4 #

```

Now what? !!!

If anyone can help with this issue in any way, please make a sign. I really miss my sounds... :(  

Thanks.

---

### Post by Tiede on 2005-02-27
Ok... I am trying yet another way.
Trying to install Alsa-driver-1.0.8

When I try it as said in the INSTALL file (i.e by running ,/configure), this is what happens:
```

root@Linuxed:/usr/src/alsa/alsa-driver-1.0.8 # ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
root@Linuxed:/usr/src/alsa/alsa-driver-1.0.8 #

```

Does someone know why this is happening?

---

### Post by Tiede on 2005-02-28
Ok. I installed gcc and this is what happens
```

....
checking for directory with kernel build... /lib/modules/2.6.8.1-3-386/build
checking for kernel version... The file /lib/modules/2.6.8.1-3-386/source/includ e/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.8.1-3-386/source).

```

When I put the appropriate directory fo the kernel, I have
```

checking for directory with kernel source... /usr
checking for directory with kernel build... /lib/modules/2.6.8.1-3-386/build
checking for kernel version... 2.6.0-test7
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 3.3.4 (Debian 1:3.3.4-9ubuntu5)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "yes"
configure: error: You have built-in ALSA in your kernel.
root@Linuxed:/usr/src/alsa/alsa-driver-1.0.8 #

```

Last time I uninstalled alsa, it crashed the GDM. Is there a way to uninstall it without affecting the GDM or to prevent its detection?

Please help.

---

### Post by Tiede on 2005-03-01
OK, I installed Alsa 1.0.8 but still no sound. here is  a log of the messages I got at install:
```

root@Linuxed:/usr/src/alsa/alsa-driver-1.0.8 # ./configure --with-kernel=/usr/include/linux
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.8
checking cross compile...
checking for directory with kernel source... /usr/include/linux
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
cat: /usr/include/linux/include/linux/kmod.h: No such file or directory
checking for kernel linux/compiler.h... "no"
Creating a dummy <linux/compiler.h>...
checking for kernel linux/pm.h... "no"
Creating a dummy <linux/pm.h>...
checking for kernel linux/spinlock.h... "no"
Creating a dummy <linux/spinlock.h>...
checking for kernel linux/irq.h... "no"
Creating a dummy <linux/irq.h>...
checking for kernel linux/threads.h... "no"
Creating a dummy <linux/threads.h>...
checking for kernel linux/rwsem.h... "no"
Creating a dummy <linux/rwsem.h>...
checking for kernel linux/gameport.h... "no"
Creating a dummy <linux/gameport.h>...
checking for kernel linux/devfs_fs_kernel.h... "no"
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... "no"
Creating a dummy <linux/highmem.h>...
checking for kernel linux/workqueue.h... "no"
checking for kernel linux/dma-mapping.h... "no"
checking for kernel asm/hw_irq.h... "no"
Creating a dummy <asm/hw_irq.h>...
checking for kernel linux/device.h... "no"
checking for kernel linux/jiffies.h... "no"
checking for kernel linux/compat.h... "no"
checking for kernel linux/adb.h... "no"
Creating <linux/adb.h>...
checking for kernel linux/cuda.h... "no"
Creating <linux/cuda.h>...
checking for kernel linux/pmu.h... "no"
Creating <linux/pmu.h>...
checking for kernel linux/moduleparam.h... "no"
checking for kernel linux/syscalls.h... "no"
checking for kernel linux/firmware.h... "no"
Creating <linux/firmware.h>...
checking for exported symbol dump_stack... grep: /usr/include/linux/kernel/ksyms.c: No such file or directory
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
Symlinking <linux/isapnp.h>...
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
checking for which soundcards to compile driver for... all
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

```

Sorry for the length...
Is there something wrong here. And if yes, what should I do?


Please help if you can.

---

### Post by Tiede on 2005-03-02
Here is the outpost of ** ls -al /usr/src **
There is no line about alsa in it. Is this normal?

```

marc@Linuxed:~ $ ls -al /usr/src
total 12
drwxrwsr-x    3 root     src          4096 2005-03-02 04:26 .
drwxr-xr-x   12 root     root         4096 2005-03-02 03:05 ..
drwxr-xr-x    7 root     root         4096 2005-03-02 04:26 rpm
marc@Linuxed:~ $

```

EDIT: I found that command while searching for a solution in [ there ](http://ubuntuforums.org/showthread.php?t=6101&page=1&pp=10)

---

### Post by andremarcel on 2005-04-24
Hello. I have solved the same Problem with my AWE32.
After modprobing I selected in the Gnome Multimedia System the ALSA Sound Driver.
Perhaps it works for you.

andremarcel

---

### Post by Tiede on 2005-04-28
Thanks for the reply. But I just fix it...
After I did this
Use the BIOS or pnp tools to set up the card and manually load module "snd_sbawe": sudo gedit /etc/modules snd_sbawe isapnp=1
as found in [ There ](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsSoundCards)
and it still did not work, I remembere reading something about IRQ conflicts and went in the BIOS, disable Plug n Play... Now sound works like a charm!
Thanks every one for the help you gave me with fixing this issue!

---

### Post by Tiede on 2005-08-09
Well, here I am back again, as my soundcard is again broken. I am not sure if this is only a Hoary-related question, but after I upgraded to Hoary two nights ago, my soundcard is working half way....It plays system sounds, but I do not hear any sound in any of the media players, for any type of multimedia files... It's like if soemthing was mute all of a sudden.
Here is the Question: Does the SoundBlaster Awe64 Card work only under Warty and not under Hoary?... 
I looked at the [ SoundCard Compatibility List ](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards) and I see Warty under ubuntu version. does this mean it only work for it, or the snd_sbawe manual loading problem does not concern Hoary cause it works on it without it?
Thanks for your replies.

---

### Post by Tiede on 2005-08-11
GOOD NEWS!
For everyone who got sounds problems after upgrading to Hoary, tryi this in a terminal
killall esd
If soud works then, follow [ this How To ](http://ubuntuforums.org/showthread.php?t=26567)

---

### Post by tofirius on 2005-08-17
Hello! This has been a very useful post for me. Thank you! However, I'm still having an issue. If I add the snd-sbawe to my modules file, it will kill my net card when ubuntu finishes loading completely w/gnome & everything. BUT, if I don't add that line to the modules, I can follow your directions of modprobe-ing in terminal & get sound & net card service... but gnome doesn't use the sound... unless I log out of gnome & log back in. Other multimedia programs (i.e. XMMS) can use the sound card no problem, in this instance.

Any ideas? I have an SBAWE32, chipset CT1745A-TBP ( 9628 ) & CT8903-DAQ ( 642D ).

Thank you!
~tofirius


> **for_usenet]So if you look through /lib/modules/2.6.8.1-4-686/kernel/ and its subdirectories, you
should find a module named snd-sbawe.ko, or something similar.  Then, if you modprobe
this module with the parameters you got, it might just work  said:**
> http://ubuntuguide.org/#sorrynomixer[/url]

cheers

---

### Post by tofirius on 2005-08-17
So... by upgrading to the latest linux kernel, the conflict was eliminated.

Cool!

~t

---

### Post by 471v3 on 2005-08-21
Oh ... I'm tired with all this shit. It has been 2 week and my fu**** Sound Blaster AWE64 doesn't work at all. God please gimme a sign  ](*,)

---

### Post by Tiede on 2005-08-22
Dont' despair 471v3.
Did you follow everything said in this thread?
Try it out and then tell us where it is you are stuck. Otherwise, we can't do any much help ;)
[ This post especiallly ](http://www.ubuntuforums.org/showpost.php?p=151549&postcount=25) might just do the trick

---

### Post by elglas on 2005-09-28
[QUOTE=daveiler]I have an ISA AWE64 Value I'm used to this by now
[alsa page for us](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+64+Value.&chip=sb16%2C+emu8000&module=sbawe) 
short version
sudo -s
modprobe snd-sbawe;modprobe snd-pcm-oss;
modprobe snd-mixer-oss;modprobe snd-seq-oss
use volume control to turn up :)
try it out :)[/QUOTE]
this worked perfectly for me, ty
(if you live near the kitchener ontario, I owe you a coffee)

---

### Post by le0buntu on 2005-10-01
Changing the BIOS setting 'PNP OS Installed' to 'No' enabled sound for me with an ISA AWE64.

That was after adding 'snd_sbawe isapnp=1' to '/etc/modules'.

- Thanks
 Leo

---

### Post by trash on 2005-12-04
[QUOTE=brousch]I have been trying to get my SB16 ISA card to work for a while. This is what finally worked for me last night:

In  */etc/modules* I added the line:
sb io=0x220 irq=5 dma=1 dma16=3

I then reinstalled all relevant alsa, oss, alsa-oss, and sound packages through Synaptic.

The sound came right up when I rebooted.

I would like to thank For_Usenet for the solution that finally worked for me![/QUOTE]

Thanks, this worked for me with a ct2230 sb16 card... running Breezy:)

---

### Post by abel on 2006-02-24
In /etc/modules I added the line:
sb io=0x220 irq=5 dma=1 dma16=3

Thank you . Nood here. I was having the same issues. An old ISA awe64 sound card.

I got into Terminal mode and used:

"sudo nano /etc/modules"


to add the line of code. "sbawe" doidn't work but "sb" did.

thanks

:mrgreen:

---

