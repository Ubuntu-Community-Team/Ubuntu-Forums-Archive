---
title: "OSS, New Sound Card, or Another Idea?"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by jrc on 2005-04-19
Any ideas on what I should try next?  My Conexant Riptide sound card is not supported by Ubuntu.  This was no surprise to me since I had been studying the sound card issue before I loaded Warty Warthog 4.10.  I thought I could solve the problem by loading a Linuxant driver for Riptide audio devices, but a Linuxant technician told me that the driver does not work with 2.6.x versions of the Linux kernel.  

I next tried to load 4Front Technologies' Open Sound System (OSS), which supports the Conexant Riptide sound card, but my attempt failed.  OSS provided me with a log describing the reasons for the failure, but I'm not yet sophisticated enough in the ways of Linux to know how to solve the problems described (a copy of the log is at the end of this message).  I asked a 4Front Technologies technician about the failure, and he replied that I needed to fix up my Linux OS environment and install the kernel development and c compilation packages.  This meant nothing at all to me.  He might as well have been speaking Greek.

So, my questions are:
(1) Is there anyone out there who has the patience to walk me through the steps I need to take to get OSS to load? or
(2) Is there anyone out there who has another idea for getting my Riptide sound card to work?

Thanks.

Here's a copy of my OSS soundconf.log:

Sat Apr 16 22:00:24 EDT 2005
Kernel version: Linux dhcppc0aland 2.6.8.1-5-386 #1 Mon Mar 14 21:44:04 UTC 2005 i686 GNU/Linux
Modutils version: 3.1-pre2
 22:00:24 up 15 min,  2 users,  load average: 0.00, 0.09, 0.09
=== Running ./bin/soundconf ===
Install directory: /usr/lib/oss
Will use /usr/bin/ld for linking.
Will use /usr/bin/ld for linking.
ln: `/lib/modules/2.6.8.1-5-386/source': File exists
No /lib/modules/2.6.8.1-5-386/build/.config
Cannot use the kbuild method
No C development tools installed.
No sndshield module available.
OSS/Linux kernel module not available. Cannot continue.

---

### Post by andvaranaut on 2005-04-19
Hmm. I don't know a thing about OSS. However, for starters, you should install the linux-headers-386 package matching your kernel. This will provide the 'build/.config' file that OSS is looking for. 

Try again. If it still complains, try installing the build-essential package, which will install a (very minimal) set of tools including make and the C and C++ compilers.

If you can get to the point where the compilation starts, it should all be relatively easy. After finding any unmet dependencies (probably there won't be any), a kernel module should be built. You will then be able to insmod it and hear your soundcard.

Good luck!

---

### Post by jrc on 2005-04-20
Thanks for your advice, andvaranaut.  I loaded both the linux-headers-386 package and the build-essential package.  I still wasn't successful in my attempt to install OSS, but at least I'm getting a different message now.  Here's the message:

Checking for any previously installed sound drivers... Done.
Couldn't dlopen /tmp/./ui_X.so
libgtk-1.2.so.0: cannot open shared object file: No such file or directory
OSS/Linux kernel module not available. Cannot continue.
Please try to install OSS again.


Do you have any more suggestions, or is it time for me to go back to the 4Front Technologies technician and ask him what's going on?

jrc

---

### Post by andvaranaut on 2005-04-21
Well, we're getting somewhere ;) That's when I was referring to above when I talked about dependencies.

You see, in order to build a package from source you need to have several libraries/tools installed. (That's "dependencies"). In this case, you can't continue building the module because the build process is not able to find the file 'libgtk-1.2.so.0', which is a shared library, kind of like a DLL in Windows (the .so bit in the filename is a hint).

To build the module you need to install a package which provides libgtk-1.2.so.0. If you are not used to fiddling around with libraries, the best way to find it is to go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and scroll to the "Search the contents of packages". Type libgtk-1.2.so.0 and click Search. You will be presented by a list of packages which contain the file you want.

In this case, the database gives two possibilities: libgtk1.2 and libgtk1.2-dbg. The -dbg packages are only for debug purposes and usually are not useful. That gives libgtk1.2 as the package name to install.

Open Synaptic and search for libgtk1.2. You will see 5 packages suggested: libgtk1.2, libgtk1.2-common, libgtk1.2-dbg, libgtk1.2-dev and libgtk1.2-doc. Mark libgtk1.2 for installation, which will probably also select libgtk1.2-common automatically. Then, mark also the libgtk1.2-dev package. Install the packages.

Then, try building the module again. If all goes well, fine. If not, the install will probably have complained about another .so file. Repeat the steps above until you get rid of all the .so errors (or you get stuck ;))

A last note. You will have noted that in addition to the package containing the library itself the -dev package has also been selected. Why? Well, when you want to run a program which uses a library, the library file (base package) is enough. However, if you were to build the same program from source, there are some other files which are needed, such as an 'index' to match functions used in the program with their location in the library. These files, which are used by the compiler to create the final program, are located in the -dev packages. So, since you are building the OSS module from source, you must also install the -dev packages of any extra libraries that you install. To be honest, I don't *think* that you need the -dev package for this particular case, as it seems that it is only used in some kind of helper to the installation and not in the build itself. But it is good practice to install the -devs when building from source, and this rule of thumb will be useful for you in case you need to install more libraries.

I hope I've made myself clear enough ;) Don't hesitate to ask if you have another problem. Good luck!

---

### Post by jrc on 2005-04-23
Andvaranaut, once again you have provided great guidance.  I followed the steps you outlined and succeeded in installing OSS.  I ran the OSS test program and sound was produced!

Unfortunately I only seem to get sound with the test program and nothing else.  When I try playing a CD I hear about a second of music and then the sound stops even though it appears that the CD keeps playing.

If you have any suggestions I'll be glad to hear them, but I also understand that since you're not familiar with OSS you may not be able to offer any further assistance.  I can always post a question in 4Front Technologies' OSS forum and see if anyone has a suggestion.

In any event, I want to thank you for your help and patience.  You're an angel.

JRC

---

### Post by andvaranaut on 2005-04-24
Hi, 
> **jrc]Andvaranaut, once again you have provided great guidance.  I followed the steps you outlined and succeeded in installing OSS.  I ran the OSS test program and sound was produced![/quote]

Hooray! :)

> 
Unfortunately I only seem to get sound with the test program and nothing else.  When I try playing a CD I hear about a second of music and then the sound stops even though it appears that the CD keeps playing.

If you are playing a CD via the drive (ie. you are using an audio-CD player program), the fact that the sound goes 'off' does not have much to do with OSS. The sound from an audio CD goes directly to the soundcard via a cable said:**
> 
If you have any suggestions I'll be glad to hear them, but I also understand that since you're not familiar with OSS you may not be able to offer any further assistance.  I can always post a question in 4Front Technologies' OSS forum and see if anyone has a suggestion.
Indeed, I'm sure the people over at the OSS forum will be able to help you better than I do...

However, I do have some suggestions. First, is this your only sound card, or do you have any other? Note that some devices, notably TV tuner cards, are detected as sound cards by ALSA (the kernel sound architecture). By default, the system uses the very first soundcard it detects; it might be that the 'everything else' is not writing to your newly-detected soundcard, but to some other place.

It could also be that there is a problem with the OSS module. As you probably know, the Linux equivalent of a driver is a kernel module. What you have done is building a custom kernel module so that the kernel knows about your soundcard. When a kernel module is loaded, it emits some messages to the system logs. These messages can help with troubleshooting the module.

The relevant log messages can be seen by typing **dmesg**. Compare the dmesg results before and after loading the OSS module. Is there any error? A /dev/dsp device should be created; is it /dev/dsp1 or any other non-standard possibility? Post the differences between dmesg's (or the whole dmesg after loading the module, if you are unable to do that) and we'll see ;)

But post also in the OSS forums. It might be something very simple that I have not thought of - I'm not that used to OSS, after all ;)
> 
In any event, I want to thank you for your help and patience.  You're an angel.


You're very much welcome :) Good luck!

---

### Post by jrc on 2005-04-29
Hello, Andvaranaut.  It has taken me a few days to find enough time to follow up on your suggestions.  

To answer the first question in your last reply to me, I only have one sound card.

OSS supplies a "soundon.log" which records any problems encountered when I try to activate OSS (I do that by issuing the "soundon" command when I'm logged in as root). The soundon.log appends a dmseg printout to the end of the log.  This is a huge document, and just looking at it makes my head spin.  I see error messages in the text, but as usual I'm not sure how to address the errors identified.  At the risk of exhausting your patience I'm posting the entire contents of the log below.  As always, any suggestions you have will be much appreciated.  I'll also try sending the log to the 4Front Technologies people to see if they can offer any suggestions.  Here's the log:

OSS version: 3.99.2c
OSS build: 200504141619
Kernel version: Linux dhcppc0aland 2.6.8.1-5-386 #1 Mon Mar 14 21:44:04 UTC 2005 i686 GNU/Linux
Kernel vermagic: 2.6.8.1-5-386 preempt 386 gcc-3.3
Modutils version: 3.1-pre2
 22:32:46 up 26 min,  2 users,  load average: 0.29, 0.30, 0.16
=== Running /usr/lib/oss/bin/soundon ===
Install directory: /usr/lib/oss
Kernel: "2.6.8.1-5-386 preempt 386 gcc-3.3 "
OSS: "2.6.8.1 preempt 386 gcc-3.3 "
Kernel and OSS module versions do not match. Removing the modules.
Will use /usr/bin/ld for linking.
make -C /lib/modules/`uname -r`/source scripts scripts_basic include/linux/version.h
make[1]: Entering directory `/usr/src/linux-headers-2.6.8.1-5-386'
make[1]: Nothing to be done for `scripts_basic'.
make[1]: `include/linux/version.h' is up to date.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.8.1-5-386'
make -C /lib/modules/`uname -r`/source SUBDIRS=/usr/lib/oss/kbuild CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.8.1-5-386'
  CC [M]  /usr/lib/oss/kbuild/osslinux.o
  Building modules, stage 2.
  MODPOST
*** Warning: "oss_checksum" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_init_module" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "touch_mixer" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_version_string" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_cardlist" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_cleanup_module" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "num_mididevs" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_mixer_ext" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "mixer_ext_set_enum" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
  CC      /usr/lib/oss/kbuild/osslinux.mod.o
  LD [M]  /usr/lib/oss/kbuild/osslinux.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.8.1-5-386'
rm -f *.o *.ko *.mod.c
The kbuild method worked OK
/usr/bin/ld -r -o /usr/lib/oss/modules/osslinux /usr/lib/oss/modules/sndshield /usr/lib/oss/modules/soundbase /usr/lib/oss/modules/uart401 /usr/lib/oss/modules/opl3 /usr/lib/oss/modules/riptide -L./lib -ldrivers
Loading OSS/Linux module
==== About to start the driver using the following config ===
# Use soundconf to edit this file.
/SECUREAUDIO OFF
/PCIIRQ 15
/IRQEXCLUDE 3 4
/DMAEXCLUDE 2
-PCI4310127a #Conexant Riptide PCI (Linux Only)
RIPTIDE ON
++ pnpres.dat ++
++++
Config option 'softoss_disable=0' defined
mk_sp_file: mknod failed
/dev/sndstat: File exists
cat: /dev/sndstat: No such file or directory


++++
crw-rw-rw-    1 root     root      14,  14 2005-04-29 22:32 /dev/dsp
crw-rw-rw-    1 root     root      14,   3 2005-04-29 22:32 /dev/dsp0
crw-rw-rw-    1 root     root      14,  19 2005-04-29 22:32 /dev/dsp1
crw-rw-rw-    1 root     root      14, 163 2005-04-29 22:32 /dev/dsp10
crw-rw-rw-    1 root     root      14, 179 2005-04-29 22:32 /dev/dsp11
crw-rw-rw-    1 root     root      14, 195 2005-04-29 22:32 /dev/dsp12
crw-rw-rw-    1 root     root      14, 211 2005-04-29 22:32 /dev/dsp13
crw-rw-rw-    1 root     root      14, 227 2005-04-29 22:32 /dev/dsp14
crw-rw-rw-    1 root     root      14, 243 2005-04-29 22:32 /dev/dsp15
crw-rw-rw-    1 root     root      14,  35 2005-04-29 22:32 /dev/dsp2
crw-rw-rw-    1 root     root      14,  51 2005-04-29 22:32 /dev/dsp3
crw-rw-rw-    1 root     root      14,  67 2005-04-29 22:32 /dev/dsp4
crw-rw-rw-    1 root     root      14,  83 2005-04-29 22:32 /dev/dsp5
crw-rw-rw-    1 root     root      14,  99 2005-04-29 22:32 /dev/dsp6
crw-rw-rw-    1 root     root      14, 115 2005-04-29 22:32 /dev/dsp7
crw-rw-rw-    1 root     root      14, 131 2005-04-29 22:32 /dev/dsp8
crw-rw-rw-    1 root     root      14, 147 2005-04-29 22:32 /dev/dsp9
lrwxrwxrwx    1 root     root            8 2005-04-29 22:32 /dev/dsp_mmap -> /dev/dsp
lrwxrwxrwx    1 root     root           10 2005-04-29 22:32 /dev/dspW -> /dev/dspW0
crw-rw-rw-    1 root     root      14,   5 2005-04-29 22:32 /dev/dspW0
crw-rw-rw-    1 root     root      14,  21 2005-04-29 22:32 /dev/dspW1
crw-rw-rw-    1 root     root      14, 165 2005-04-29 22:32 /dev/dspW10
crw-rw-rw-    1 root     root      14, 181 2005-04-29 22:32 /dev/dspW11
crw-rw-rw-    1 root     root      14, 197 2005-04-29 22:32 /dev/dspW12
crw-rw-rw-    1 root     root      14, 213 2005-04-29 22:32 /dev/dspW13
crw-rw-rw-    1 root     root      14, 229 2005-04-29 22:32 /dev/dspW14
crw-rw-rw-    1 root     root      14, 245 2005-04-29 22:32 /dev/dspW15
crw-rw-rw-    1 root     root      14,  37 2005-04-29 22:32 /dev/dspW2
crw-rw-rw-    1 root     root      14,  53 2005-04-29 22:32 /dev/dspW3
crw-rw-rw-    1 root     root      14,  69 2005-04-29 22:32 /dev/dspW4
crw-rw-rw-    1 root     root      14,  85 2005-04-29 22:32 /dev/dspW5
crw-rw-rw-    1 root     root      14, 101 2005-04-29 22:32 /dev/dspW6
crw-rw-rw-    1 root     root      14, 117 2005-04-29 22:32 /dev/dspW7
crw-rw-rw-    1 root     root      14, 133 2005-04-29 22:32 /dev/dspW8
crw-rw-rw-    1 root     root      14, 149 2005-04-29 22:32 /dev/dspW9
++++ dmesg printout follows ++++
T (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0fffd352
ACPI: FADT (v001 HP     Pandora  0x06040000 PTL  0x00000001) @ 0x0ffffb65
ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0ffffbd9
ACPI: DSDT (v001  HPHPD  Pandora 0x06040000 MSFT 0x0100000b) @ 0x00000000
ACPI: PM-Timer IO Port: 0x8008
Built 1 zonelists
Kernel command line: root=/dev/hdb1 ro quiet splash
Local APIC disabled by BIOS -- reenabling.
Found and enabled local APIC!
Initializing CPU#0
PID hash table entries: 1024 (order 10: 8192 bytes)
Detected 1007.546 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 252284k/262080k available (1337k kernel code, 9092k reserved, 731k data, 204k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1994.75 BogoMIPS
Security Scaffold v1.0.0 initialized
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000
CPU: After vendor identify, caps:  0183fbff c1c7fbff 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU: After all inits, caps:        0183fbff c1c7fbff 00000000 00000020
CPU: AMD Athlon(tm) Processor stepping 02
Enabling fast FPU save and restore... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: IRQ9 SCI: Edge set to Level Trigger.
enabled ExtINT on CPU#0
ESR value before enabling vector: 00000000
ESR value after enabling vector: 00000000
Using local APIC timer interrupts.
calibrating APIC timer ...
..... CPU clock speed is 1006.0883 MHz.
..... host bus clock speed is 201.0376 MHz.
checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Freeing initrd memory: 4136k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd80c, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20040816
spurious 8259A interrupt: IRQ7.
    ACPI-1133: *** Error: Method execution failed [\_SB_.PCI0.PIB_.SIO0._INI] (Node cfba7520), AE_AML_UNINITIALIZED_LOCAL
    ACPI-1133: *** Error: Method execution failed [\_SB_.PCI0.PIB_.SIO0.LPT_._INI] (Node cfba71a0), AE_AML_UNINITIALIZED_LOCAL
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 9 10 *11 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PPB_._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f8190
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xac15, dseg 0x400
pnp: 00:00: ioport range 0x294-0x297 has been reserved
pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:01: ioport range 0x8000-0x807f could not be reserved
pnp: 00:01: ioport range 0x400-0x40f has been reserved
pnp: 00:0b: ioport range 0x3400-0x347f has been reserved
PnPBIOS: 19 nodes reported by PnP BIOS; 19 recorded by driver
PCI: Using ACPI for IRQ routing
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:04.2[D] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:0e.0[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:00:0e.1[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:0f.0[A] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
ACPI: PCI interrupt 0000:01:05.0[A] -> GSI 11 (level, low) -> IRQ 11
Simple Boot Flag at 0x36 set to 0x1
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
PCI: Disabling Via external APIC routing
PCI: Via IRQ fixup for 0000:00:04.2, from 9 to 11
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 3
Cannot allocate resource for EISA slot 8
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP: Hash tables configured (established 16384 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
ACPI: (supports S0 S1 S5)
ACPI wakeup devices:
PCI0  KBC USB0 USB1
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4136 blocks [1 disk] into ram disk... \
\
done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 204k freed
vesafb: probe of vesafb0 failed with error -6
ACPI: Processor [CPU0] (supports C1)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:04.1
VP_IDE: chipset revision 16
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt82c686a (rev 21) IDE UDMA66 controller on pci0000:00:04.1
    ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:pio, hdb:DMA
    ide1: BM-DMA at 0x1008-0x100f, BIOS settings: hdc:pio, hdd:DMA
hda: Maxtor 96147U8, ATA DISK drive
hdb: Maxtor 6B200P0, ATA DISK drive
Using anticipatory io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 120060864 sectors (61471 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(66)
 /dev/ide/host0/bus0/target0/lun0: p1
hdb: max request size: 1024KiB
hdb: 398297088 sectors (203928 MB) w/8192KiB Cache, CHS=24792/255/63, UDMA(66)
 /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >
hdc: LG CD-RW CED-8080B, ATAPI CD/DVD-ROM drive
hdd: Pioneer DVD-ROM ATAPIModel DVD-115 0111, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 497972k swap on /dev/hdb5.  Priority:-1 extents:1
EXT3 FS on hdb1, internal journal
mice: PS/2 mouse device common for all mice
hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI DVD-ROM drive, 512kB Cache, UDMA(33)
parport0: PC-style at 0x378 [PCSPP,EPP]
parport_pc: Via 686A parallel port: io=0x378
lp0: using parport0 (polling).
Capability LSM initialized
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.8.1-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected AMD Irongate chipset
agpgart: Maximum main memory to use for agp memory: 203M
agpgart: AGP aperture is 64M @ 0xf8000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: PCI Express Hot Plug Controller Driver version: 0.4
shpchp: HPC vendor_id 1022 device_id 7007 ss_vid 0 ss_did 0
shpchp: shpc_init: cannot reserve MMIO region
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:04.2[D] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:04.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:04.2: irq 11, io base 00001020
uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using address 2
usb 1-2: new full speed USB device using address 3
hub 1-2:1.0: USB hub found
hub 1-2:1.0: 3 ports detected
usb 1-2.1: new full speed USB device using address 4
usbcore: registered new driver hiddev
input: USB HID v1.00 Keyboard [HP Multimedia Keyboard Hub] on usb-0000:00:04.2-2.1
input,hiddev96: USB HID v1.00 Device [HP Multimedia Keyboard Hub] on usb-0000:00:04.2-2.1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1204
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
usb 1-2.3: new low speed USB device using address 5
input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:04.2-2.3
ts: Compaq touchscreen protocol output
8139too Fast Ethernet driver 0.9.27
PCI: Enabling device 0000:00:0f.0 (0000 -> 0003)
ACPI: PCI interrupt 0000:00:0f.0[A] -> GSI 11 (level, low) -> IRQ 11
eth0: RealTek RTL8139 at 0x1400, 00:10:b5:6c:7c:5c, IRQ 11
eth0:  Identified 8139 chip type 'RTL-8139B'
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02cc0c0(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ip_tables: (C) 2000-2002 Netfilter core team
ip_conntrack version 2.1 (2047 buckets, 16376 max) - 296 bytes per conntrack
eth0: no IPv6 routers present
drivers/usb/input/hid-input.c: event field not found
drivers/usb/input/hid-input.c: event field not found
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.148.129.99 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=16395 DF PROTO=TCP SPT=2997 DPT=135 WINDOW=64240 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.67.40 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=39018 DF PROTO=TCP SPT=4938 DPT=135 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.67.40 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=39129 DF PROTO=TCP SPT=4938 DPT=135 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.119.66 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=64834 DF PROTO=TCP SPT=3249 DPT=139 WINDOW=64512 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.119.66 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=1144 DF PROTO=TCP SPT=3249 DPT=139 WINDOW=64512 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.1.254 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=33537 DF PROTO=TCP SPT=4733 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.1.254 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=33763 DF PROTO=TCP SPT=4733 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=63.230.18.51 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=8092 DF PROTO=TCP SPT=1029 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.119.66 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=11630 DF PROTO=TCP SPT=2249 DPT=139 WINDOW=64512 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.119.66 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=13439 DF PROTO=TCP SPT=2249 DPT=139 WINDOW=64512 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.0.112 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=29908 DF PROTO=TCP SPT=1116 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.0.112 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=30281 DF PROTO=TCP SPT=1116 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=200.78.47.11 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=39188 DF PROTO=TCP SPT=4965 DPT=139 WINDOW=16384 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=200.78.47.11 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=39619 DF PROTO=TCP SPT=4965 DPT=139 WINDOW=16384 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.1.142 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=39919 DF PROTO=TCP SPT=2652 DPT=135 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.1.142 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=40338 DF PROTO=TCP SPT=2652 DPT=135 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.162.35.118 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=3350 DF PROTO=TCP SPT=3734 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.162.35.118 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=3649 DF PROTO=TCP SPT=3734 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.0.112 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=43547 DF PROTO=TCP SPT=4544 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.0.112 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=43980 DF PROTO=TCP SPT=4544 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.1.36 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=52472 DF PROTO=TCP SPT=4770 DPT=135 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.1.36 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=52619 DF PROTO=TCP SPT=4770 DPT=135 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.0.130 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=12623 DF PROTO=TCP SPT=3195 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.0.130 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=12997 DF PROTO=TCP SPT=3195 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
IN=eth0 OUT= MAC=00:10:b5:6c:7c:5c:00:a0:c5:c3:aa:bc:08:00 SRC=68.167.4.124 DST=172.16.1.10 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=1473 DF PROTO=TCP SPT=1517 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
osslinux: module license 'Open Sound System' taints kernel.
++++++++
0000:00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
        Flags: bus master, medium devsel, latency 32
        Memory at f8000000 (32-bit, prefetchable)
        Memory at f4012000 (32-bit, prefetchable) [size=4K]
        I/O ports at 1010 [disabled] [size=4]
        Capabilities: [a0] AGP version 1.0

0000:00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=86
        Memory behind bridge: f5000000-f5ffffff
        Prefetchable memory behind bridge: fc000000-fdffffff

0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 21)
        Subsystem: Asustek Computer, Inc.: Unknown device 8006
        Flags: bus master, stepping, medium devsel, latency 0

0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
        Flags: bus master, medium devsel, latency 32
        I/O ports at 1000 [size=16]
        Capabilities: [c0] Power Management version 2

0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 1020 [size=32]
        Capabilities: [80] Power Management version 2

0000:00:04.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)        Flags: medium devsel, IRQ 9
        Capabilities: [68] Power Management version 2

0000:00:0e.0 Multimedia audio controller: Rockwell International: Unknown device 4310
        Subsystem: Risq Modular Systems, Inc.: Unknown device 4310
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 1040
        Capabilities: [40] Power Management version 1

0000:00:0e.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
        Subsystem: Risq Modular Systems, Inc.: Unknown device 4311
        Flags: medium devsel, IRQ 10
        Memory at f4000000 (32-bit, non-prefetchable) [disabled]
        Capabilities: [40] Power Management version 1

0000:00:0e.2 Input device controller: Rockwell International: Unknown device 4312
        Subsystem: Risq Modular Systems, Inc.: Unknown device 4312
        Flags: medium devsel
        Memory at f4010000 (32-bit, non-prefetchable) [disabled]
        Capabilities: [40] Power Management version 1

0000:00:0f.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
        Subsystem: Hewlett-Packard Company: Unknown device 9207
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 1400
        Memory at f4011000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:01:05.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15) (prog-if 00 [VGA])
        Subsystem: Asustek Computer, Inc. AGP-V3800 SDRAM
        Flags: bus master, 66MHz, medium devsel, latency 40, IRQ 11
        Memory at f5000000 (32-bit, non-prefetchable)
        Memory at fc000000 (32-bit, prefetchable) [size=32M]
        Capabilities: [60] Power Management version 1
        Capabilities: [44] AGP version 2.0

++++++++
Bus 001 Device 005: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 004: ID 03f0:020c Hewlett-Packard Multimedia Keyboard
Bus 001 Device 003: ID 03f0:010c Hewlett-Packard Multimedia Keyboard Hub
Bus 001 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 001 Device 001: ID 0000:0000
++++++++
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 4
model name      : AMD Athlon(tm) Processor
stepping        : 2
cpu MHz         : 1007.546
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow
bogomips        : 1994.75

++++
           CPU0
  0:    1598614          XT-PIC  timer
  1:          9          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  8:          1          XT-PIC  rtc
  9:          0          XT-PIC  acpi
 10:          1          XT-PIC  RIPTIDE
 11:      85703          XT-PIC  uhci_hcd, eth0
 14:       8682          XT-PIC  ide0
 15:      27942          XT-PIC  ide1
NMI:          0
LOC:    1598554
ERR:       1908
MIS:          0
Redirecting /usr/lib/libasound.so.2 -> libsalsa

---

### Post by MasterPatricko on 2005-07-04
Did you use the riptide drivers from Linuxant? Because I cant get them to work. If you could outline how you installed them, it would be a great help  ;-)

---

