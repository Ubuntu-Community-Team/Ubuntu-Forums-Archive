---
title: "howto patch alan cox to ubuntu linux?"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by man_exec on 2005-07-05
I've got Warty up and running just great.  However, I can't get my **ITE 8212** card recognized in ATA or RAID modes.  ***Alan Cox*** has a patch for the driver built into his patchset.  I've used it before with SourceMage, so I know it works.

Can someone please provide this noob (me) with some fairly detailed instructions on how to:


[list=1]
[*]select the correct ubuntu linux headers, source files, image, etc.
[*]select the correct ac patchset
[*]insert the patch
[*]compile the kernel
[*]insert new kernel entry into grub
[*]any other compiles (alsa, etc) that become necessary after recompiling the kernel
[/list]Thanks all!
:???:

---

### Post by keikoz on 2005-07-14
Well i've had the exactly same problem: the IT8212 ide-raid controller on an Asus P5GDC-Deluxe mobo. I worked hard for 3 nights to make it working; i'll give you the way i used, It isn't perfect (i have some errors in dmesg), but it works fine in fact.

1. Use the generic kernel instead of the ubuntu kernel; i can't find the way to patch the linux-source of ubuntu with the -ac patch: the compilation process failes everytime; i installed the same version kernel i have (2.6.10) but generic from [ftp://ftp.kernel.org/pub/linux/kernel/v2.6/](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/)

copy it in /usr/src and de-archive it:
cp -r ....../linux-2.6.10.tar.bz2 /usr/src
cd /usr/src
tar jxvf linux-2.6.10.tar.bz2
remove the old symlink (if there is one) and create a new one:
cd /usr/src
rm linux
ln -s 

2. The Alan Cox patch; i just took the last one, for my kernel (ac12) on [http://kernel.org/pub/linux/kernel/people/alan/](http://kernel.org/pub/linux/kernel/people/alan/) . Taking the last revision for your kernel should work (for me it was [http://kernel.org/pub/linux/kernel/people/alan/linux-2.6/2.6.10/patch-2.6.10-ac12.bz2)](http://kernel.org/pub/linux/kernel/people/alan/linux-2.6/2.6.10/patch-2.6.10-ac12.bz2)).
Patch the kernel:
cd /usr/src/linux
gzip -dc patch-2.6.10-ac12.bz2 | patch -p1

3. For the compilation i just used the [debian-method](https://wiki.ubuntu.com//KernelCompileHowto), using make-kpkg (but not using the standard ubuntu kernel-source, like this:
# apt-get install gcc kernel-package

# cd /usr/src/linux
# cp /boot/config-2.6.10-5-383 .config
# make oldconfig
you will have to answer to some questions here... if you dont know what to answer there... i answered "no" to anything except the first (i answered 1000); dont know how it will be in your case :o)
Now configuring:
# make gconfig <== you need gtk2 for using it and some other librairies: check the output messages if it doesnt work
There inside you can configure anything you want; the easiest way is to just activating your controller: go in Device Drivers--> ATA/ATAPI... Support --> Enhanced... --> PCI IDE Chipset Support --> Generic PCI ... :
there you activate the IT821x: cilck on M for a module or Y for compilating it in the kernel (in both case it will find it on boot)
Save the modification and exit 

Now compile:
# make-kpkg clean
# make-kpkg --initrd --stem linux --revision=custom.1.0 kernel_image
That will create a .deb package 

Install it:
# cd ..
# dpkg -i linux-image-2.6.8.1_custom.1.0_i386.deb

4. For grub:
the new kernel will automatically be added in the grub menu.lst file: it can be usefull to edit it anyway to change some little things:
emacs /boot/grub/menu.lst
here decomment the "hiddenmenu" lines taking away the "#"
That's all, on boot you'll have the choice between your kernels

Last thing, i used this method cause i wasnt able to compile the ubuntu kernel adding the -ac patch. that mean i dont really answer to your original question, but i'm still looking about it... I will google another entire night  :roll: . If I find the way, i'll   report it here. Pls if somebody else knows how to do it, help (us)  :smile: 

keikoz

---

### Post by man_exec on 2005-07-17
[size=2]Hey keikoz, \\:D/[/size]

this worked pretty well - almost.  I really thank you for helping.  I'm almost there and that is great.  

Long story short...I followed your directions and when I boot into the new kernel, I can see all the drives on the ITE8212 controller. However, with this new kernel, I can't mount any of them AND I can no longer mount my VFAT drives on the main ide controller (which I can do, when I boot into my standart Warty kernel). Any ideas on that one? The fstab file is the same for both kernels and permissions are the same, so it's not them. Also, when I try to use a vterm (CTRL-ALT-F2), I get a mish mash of scattered colors and no black screen with a prompt. Any ideas on that one?

I had to make some minor modifications to your howto, to work on my machine.  See below.

Thanks partner,

arvan


> **keikoz]Well i've had the exactly same problem: the IT8212 ide-raid controller on an Asus P5GDC-Deluxe mobo. I worked hard for 3 nights to make it working said:**
> ftp://ftp.kernel.org/pub/linux/kernel/v2.6/[/url]

copy it in /usr/src and de-archive it:
cp -r ....../linux-2.6.10.tar.bz2 /usr/src
cd /usr/src
tar jxvf linux-2.6.10.tar.bz2
remove the old symlink (if there is one) and create a new one:
cd /usr/src
rm linux
ln -s [color=Red]**linux-2.6.10 linux**[/color]

2. The Alan Cox patch; i just took the last one, for my kernel (ac12) on [http://kernel.org/pub/linux/kernel/people/alan/]("http://kernel.org/pub/linux/kernel/people/alan/") . Taking the last revision for your kernel should work (for me it was [http://kernel.org/pub/linux/kernel/people/alan/linux-2.6/2.6.10/patch-2.6.10-ac12.bz2)]("http://kernel.org/pub/linux/kernel/people/alan/linux-2.6/2.6.10/patch-2.6.10-ac12.bz2%29").
Patch the kernel:
cd /usr/src/linux
[color=Red]**bzip2**[/color] -dc patch-2.6.10-ac12.bz2 | patch -p1

3. For the compilation i just used the [debian-method]("https://wiki.ubuntu.com//KernelCompileHowto"), using make-kpkg (but not using the standard ubuntu kernel-source, like this:
# apt-get install gcc kernel-package

# cd /usr/src/linux
# cp /boot/config-2.6.10-5-383 .config
# make oldconfig
you will have to answer to some questions here... if you dont know what to answer there... i answered "no" to anything except the first (i answered 1000); dont know how it will be in your case :o)
Now configuring:
# make gconfig <== you need gtk2 for using it and some other librairies: check the output messages if it doesnt work
There inside you can configure anything you want; the easiest way is to just activating your controller: go in Device Drivers--> ATA/ATAPI... Support --> Enhanced... --> PCI IDE Chipset Support --> Generic PCI ... :
there you activate the IT821x: cilck on M for a module or Y for compilating it in the kernel (in both case it will find it on boot)
[color=Red]**# make menuconfig  **<--- I'm more comfortable with this method, so I used it instead[/color]
Save the modification and exit 

Now compile:
# make-kpkg clean
# make-kpkg --initrd --stem linux --revision=custom.1.0 kernel_image
That will create a .deb package 

Install it:
# cd ..
# dpkg -i linux-image-2.6.8.1_custom.1.0_i386.deb

4. For grub:
the new kernel will automatically be added in the grub menu.lst file: it can be usefull to edit it anyway to change some little things:
emacs /boot/grub/menu.lst
here decomment the "hiddenmenu" lines taking away the "#"
That's all, on boot you'll have the choice between your kernels

Last thing, i used this method cause i wasnt able to compile the ubuntu kernel adding the -ac patch. that mean i dont really answer to your original question, but i'm still looking about it... I will google another entire night :roll: . If I find the way, i'll   report it here. Pls if somebody else knows how to do it, help (us)  :) 

keikoz

---

### Post by keikoz on 2005-07-17
Yes in fact the modification that you did, had to be done, i just wrote to quick :p

Actually i'm not lucky; the procedure i explained worked once; but ONLY once, for me. I can't now make the same procedure, i got a lot of error messages; and the only way to boot with the new kernel is disactivating the it8212 controller in the bios :/

Seems that the kernel need some ubuntu specific patches maybee, or i dont know what else...

I reported my pbl [there](http://ubuntuforums.org/showthread.php?t=49645)

I dont know about your pbl, but i noticed that there is a conflict problem with managing the adresses of the controllers bye the kernel, something with the IRQ or something like that (actually i'm to noob to really understand that). Past here your dmesg and the result of ls /hd* , if you can. The driver manages the new drives as ide controllers and not scsi as did the "official" driver of ITE. 

regards

keikoz

---

### Post by man_exec on 2005-07-17
Keikoz,

following your request, I've pasted my dmesg and ls /dev/hd*.

Let's see where this gets us.

arvan:?

---- dmesg -------
[indent]arvan@frankenputer:~$ dmesg
 BogoMIPS (lpj=2170880)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000020 00000000 00000000
CPU: AMD Athlon(tm) XP 3200+ stepping 00
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0e20)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfaff0, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
ACPI: PCI Interrupt Link [APC3] (IRQs *1, disabled.
ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 14 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email="bjorn.helgaas@hp.com"]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
spurious 8259A interrupt: IRQ7.
pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
pnp: 00:00: ioport range 0x1400-0x147f has been reserved
pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
pnp: 00:00: ioport range 0x1800-0x187f has been reserved
pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
pnp: 00:01: ioport range 0x1c00-0x1c3f has been reserved
pnp: 00:01: ioport range 0x2000-0x203f has been reserved
audit: initializing netlink socket (disabled)
audit(1121569245.661:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 2
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 3072k, total 262144k
vesafb: mode is 1024x768x16, linelength=2048, pages=169
vesafb: protected mode interface info at c000:573b
vesafb: scrolling: redraw
vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
fb0: VESA VGA frame buffer device
Console: switching to colour frame buffer device 128x48
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
NFORCE2: IDE controller at PCI slot 0000:00:09.0
NFORCE2: chipset revision 162
NFORCE2: not 100% native mode: will probe irqs later
NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hdaMA, hdbMA
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdcMA, hddMA
Probing IDE interface ide0...
hda: Maxtor 4D080H4, ATA DISK drive
hdb: WDC WD1200BB-00CAA1, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: Host Protected Area detected.
        current capacity is 156299375 sectors (80025 MB)
        native  capacity is 156301488 sectors (80026 MB)
hda: Host Protected Area disabled.
hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
hdb: max request size: 128KiB
hdb: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
hdb: cache flushes not supported
 /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
hdc: CRD-8400B, ATAPI CD/DVD-ROM drive
hdd: ARTEC WRR-52X 1.25 20030606, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 2650684k swap on /dev/hdb5.  Priority:-1 extents:1
EXT3 FS on hdb1, internal journal
hdc: ATAPI 48X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: PS/2 Logitech Mouse on isa0060/serio1
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email="dm-devel@redhat.com"]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS volume version 3.1.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected NVIDIA nForce2 chipset
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: AGP aperture is 64M @ 0xe0000000
i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
i2c_adapter i2c-1: nForce2 SMBus adapter at 0x2000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [LUBA] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 5 (level, low) -> IRQ 5
ohci_hcd 0000:00:02.0: nVidia Corporation nForce2 USB Controller
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 5, pci mem 0xe8003000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [LUBB] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 10 (level, low) -> IRQ 10
ohci_hcd 0000:00:02.1: nVidia Corporation nForce2 USB Controller (#2)
PCI: Setting latency timer of device 0000:00:02.1 to 64
ohci_hcd 0000:00:02.1: irq 10, pci mem 0xe8004000
ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 11 (level, low) -> IRQ 11
ehci_hcd 0000:00:02.2: nVidia Corporation nForce2 USB Controller
PCI: Setting latency timer of device 0000:00:02.2 to 64
ehci_hcd 0000:00:02.2: irq 11, pci mem 0xe8005000
ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
PCI: cache line size of 64 is not supported by device 0000:00:02.2
ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 6 ports detected
ACPI: PCI Interrupt Link [LACI] enabled at IRQ 9
PCI: setting IRQ 9 as level-triggered
ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 9 (level, low) -> IRQ 9
PCI: Setting latency timer of device 0000:00:06.0 to 64
intel8x0_measure_ac97_clock: measured 49948 usecs
intel8x0: clocking to 47475
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
ACPI: PCI interrupt 0000:01:08.0[A] -> GSI 11 (level, low) -> IRQ 11
scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 6.2.36
        <Adaptec 2940 SCSI adapter>
        aic7870: Single Channel A, SCSI Id=7, 16/253 SCBs
  
(scsi0:A:2): 8.064MB/s transfers (8.064MHz, offset 15)
  Vendor: iomega    Model: jaz 1GB           Rev: J^77
  Type:   Direct-Access                      ANSI SCSI revision: 02
(scsi0:A:5): 8.064MB/s transfers (8.064MHz, offset 15)
  Vendor: SONY      Model: SDT-9000          Rev: 0601
  Type:   Sequential-Access                  ANSI SCSI revision: 02
Attached scsi removable disk sda at scsi0, channel 0, id 2, lun 0
st: Version 20041025, fixed bufsize 32768, s/g segs 256
Attached scsi tape st0 at scsi0, channel 0, id 5, lun 0
st0: try direct i/o: yes (alignment 512 B), max page reachable by HBA 1048575
r8169 Gigabit Ethernet driver 1.2 loaded
ACPI: PCI interrupt 0000:01:0b.0[A] -> GSI 11 (level, low) -> IRQ 11
eth0: Identified chip type is 'RTL8169s/8110s'.
eth0: RTL8169 at 0xf8df6000, 00:0f:ea:38:1a:9e, IRQ 11
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:01:0e.0[A] -> GSI 11 (level, low) -> IRQ 11
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[e7006000-e70067ff]  Max Packet=[2048]
NET: Registered protocol family 17
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea0000358a00]
r8169: eth0: link up
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 805 MBytes.
ACPI: PCI Interrupt Link [LNK4] enabled at IRQ 5
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 5 (level, low) -> IRQ 5
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.
[fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[fglrx] free  AGP = 54800384
[fglrx] max   AGP = 54800384
[fglrx] free  LFB = 116387840
[fglrx] max   LFB = 116387840
[fglrx] free  Inv = 134217728
[fglrx] max   Inv = 134217728
[fglrx] total Inv = 134217728
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 16384
eth0: no IPv6 routers present
ibm_acpi: ec object not found
[/indent]--------  ls /dev/hd* -----------
[indent]arvan@frankenputer:~$ ls /dev/hd*
/dev/hda   /dev/hda2  /dev/hdb   /dev/hdb2  /dev/hdc
/dev/hda1  /dev/hda5  /dev/hdb1  /dev/hdb5  /dev/hdd
[/indent]

---

### Post by keikoz on 2005-07-17
Humm seems your devices are present in /dev, like your Hard disks:
/dev/hda and /dev/hdb are your HD, and /dev/hdc and /dev/hdd are your ATAPI cd/dvd-roms:

in your dmesg i notice:
ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hdaMA, hdbMA
ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdcMA, hddMA
Probing IDE interface ide0...
hda: Maxtor 4D080H4, ATA DISK drive
hdb: WDC WD1200BB-00CAA1, ATA DISK drive
...
Probing IDE interface ide1...
hdc: CRD-8400B, ATAPI CD/DVD-ROM drive
hdd: ARTEC WRR-52X 1.25 20030606, ATAPI CD/DVD-ROM drive

Now try just mounting your cd/dvd:
mount -t iso9660 /dev/hdc /media/cdrom
If it works you will add them in the fstab file (i'll explain you how to do it)

Another thing; I myself can't repeat the procedure i explained you (how is that possible ???). Is the procedure you described here exactly the one you used ? I'll compare with my way, and maybee find the bug...

keikoz

---

### Post by man_exec on 2005-07-18
Keikoz,

I'm a moron. I gave you the dmesg & ls /dev/hd* from the Warty kernel boot. I've rebooted into my ac-12 kernel and here they are.
 (sheesh! what a dope I am.) 

thanks,

arvan

-------- dmesg ------------

arvan@frankenputer:~$ dmesg
 K (64 bytes/line), D cache 64K (64 bytes/line)
 CPU: L2 Cache: 512K (64 bytes/line)
 CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
 CPU: AMD Athlon(tm) XP 3200+ stepping 00
 Enabling fast FPU save and restore... done.
 Enabling unmasked SIMD FPU exception support... done.
 Checking 'hlt' instruction... OK.
 ACPI: setting ELCR to 0200 (from 0e20)
 checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
 Freeing initrd memory: 4268k freed
 NET: Registered protocol family 16
 EISA bus registered
 PCI: PCI BIOS revision 2.10 entry at 0xfaff0, last bus=2
 PCI: Using configuration type 1
 mtrr: v2.0 (20020519)
 ACPI: Subsystem revision 20041105
 ACPI: Interpreter enabled
 ACPI: Using PIC for interrupt routing
 ACPI: PCI Root Bridge [PCI0] (00:00)
 PCI: Probing PCI hardware (bus 00)
 PCI: nForce2 C1 Halt Disconnect fixup
 ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
 ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
 ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
 ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
 ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
 ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
 ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
 ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
 ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
 ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
 ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
 ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
 ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
 ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
 ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
 ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
 ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
 ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
 ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
 ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
 ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
 ACPI: PCI Interrupt Link [APC3] (IRQs *1, disabled.
 ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
 ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
 ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
 ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
 ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
 ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
 ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
 ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
 ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
 ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
 ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
 ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
 ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
 Linux Plug and Play Support v0.97 (c) Adam Belay
 pnp: PnP ACPI init
 pnp: PnP ACPI: found 14 devices
 PnPBIOS: Disabled by ACPI
 PCI: Using ACPI for IRQ routing
 ** PCI interrupts are no longer routed automatically.  If this
 ** causes a device to stop working, it is probably because the
 ** driver failed to call pci_enable_device().  As a temporary
 ** workaround, the "pci=routeirq" argument restores the old
 ** behavior.  If this argument makes the device work again,
 ** please email the output of "lspci" to [email="bjorn.helgaas@hp.com"]bjorn.helgaas@hp.com[/email]
 ** so I can fix the driver.
 spurious 8259A interrupt: IRQ7.
 pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
 pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
 pnp: 00:00: ioport range 0x1400-0x147f has been reserved
 pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
 pnp: 00:00: ioport range 0x1800-0x187f has been reserved
 pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
 pnp: 00:01: ioport range 0x1c00-0x1c3f has been reserved
 pnp: 00:01: ioport range 0x2000-0x203f has been reserved
 audit: initializing netlink socket (disabled)
 audit(1121648603.904:0): initialized
 VFS: Disk quotas dquot_6.5.1
 Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
 devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
 devfs: boot_options: 0x0
 Initializing Cryptographic API
 isapnp: Scanning for PnP cards...
 isapnp: No Plug & Play device found
 serio: i8042 AUX port at 0x60,0x64 irq 12
 serio: i8042 KBD port at 0x60,0x64 irq 1
 Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
 ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
 ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
 io scheduler noop registered
 io scheduler anticipatory registered
 io scheduler deadline registered
 io scheduler cfq registered
 RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
 input: AT Translated Set 2 keyboard on isa0060/serio0
 EISA: Probing bus 0 at eisa0
 Cannot allocate resource for EISA slot 1
 Cannot allocate resource for EISA slot 2
 EISA: Detected 0 cards.
 NET: Registered protocol family 2
 IP: routing cache hash table of 8192 buckets, 64Kbytes
 TCP: Hash tables configured (established 262144 bind 65536)
 NET: Registered protocol family 8
 NET: Registered protocol family 20
 ACPI wakeup devices:
 HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1
 ACPI: (supports S0 S1 S4 S5)
 RAMDISK: cramfs filesystem found at block 0
 RAMDISK: Loading 4268KiB [1 disk] into ram disk... done.
 VFS: Mounted root (cramfs filesystem) readonly.
 Freeing unused kernel memory: 224k freed
 NET: Registered protocol family 1
 Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
 ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
 NFORCE2: IDE controller at PCI slot 0000:00:09.0
 NFORCE2: chipset revision 162
 NFORCE2: not 100% native mode: will probe irqs later
 NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
 NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hdaMA, hdbMA
     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdcMA, hddMA
 Probing IDE interface ide0...
 hda: Maxtor 4D080H4, ATA DISK drive
 hdb: WDC WD1200BB-00CAA1, ATA DISK drive
 elevator: using anticipatory as default io scheduler
 ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
 Probing IDE interface ide1...
 hdc: CRD-8400B, ATAPI CD/DVD-ROM drive
 hdd: ARTEC WRR-52X 1.25 20030606, ATAPI CD/DVD-ROM drive
 ide1 at 0x170-0x177,0x376 on irq 15
 hda: max request size: 128KiB
 hda: Host Protected Area detected.
         current capacity is 156299375 sectors (80025 MB)
         native  capacity is 156301488 sectors (80026 MB)
 hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
 hda: task_no_data_intr: error=0x04 { DriveStatusError }
 ide: failed opcode was: 0x37
 hda: 156299375 sectors (80025 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
 hda: cache flushes not supported
  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
 hdb: max request size: 128KiB
 hdb: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
 hdb: cache flushes not supported
  /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >
 IT8212: IDE controller at PCI slot 0000:01:0c.0
 ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
 PCI: setting IRQ 10 as level-triggered
 ACPI: PCI interrupt 0000:01:0c.0[A] -> GSI 10 (level, low) -> IRQ 10
 IT8212: chipset revision 17
 it821x: controller in pass through mode.
 IT8212: 100% native mode on irq 10
     ide2: BM-DMA at 0xa800-0xa807, BIOS settings: hdeio, hdfMA
     ide3: BM-DMA at 0xa808-0xa80f, BIOS settings: hdgMA, hdhio
 Probing IDE interface ide2...
 hde: WDC WD204BA, ATA DISK drive
 hdf: Maxtor 91020D6, ATA DISK drive
 ide2 at 0x9810-0x9817,0x9c02 on irq 10
 hde: max request size: 128KiB
 hde: 39876480 sectors (20416 MB) w/2048KiB Cache, CHS=39560/16/63, UDMA(66)
 hde: cache flushes not supported
  /dev/ide/host2/bus0/target0/lun0: p1
 hdf: max request size: 128KiB
 hdf: 19923120 sectors (10200 MB) w/512KiB Cache, CHS=19765/16/63, UDMA(33)
 hdf: cache flushes not supported
  /dev/ide/host2/bus0/target1/lun0: p1
 Probing IDE interface ide3...
 hdg: QUANTUM FIREBALL_TM3840A, ATA DISK drive
 ide3 at 0xa010-0xa017,0xa402 on irq 10
 hdg: max request size: 128KiB
 hdg: 7539840 sectors (3860 MB) w/76KiB Cache, CHS=7480/16/63, DMA
 hdg: cache flushes not supported
  /dev/ide/host2/bus1/target0/lun0: p1
 EXT3-fs: mounted filesystem with ordered data mode.
 kjournald starting.  Commit interval 5 seconds
 Adding 2650684k swap on /dev/hdb5.  Priority:-1 extents:1
 EXT3 FS on hdb1, internal journal
 hdc: ATAPI 48X CD-ROM drive, 128kB Cache
 Uniform CD-ROM driver Revision: 3.20
 hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
 parport: PnPBIOS parport detected.
 parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
 lp0: using parport0 (interrupt-driven).
 mice: PS/2 mouse device common for all mice
 input: PS/2 Logitech Mouse on isa0060/serio1
 ieee1394: Initialized config rom entry `ip1394'
 SCSI subsystem initialized
 sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
 ts: Compaq touchscreen protocol output
 device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email="dm-devel@redhat.com"]dm-devel@redhat.com[/email]
 md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
 device-mapper: dm-linear: Device lookup failed
 device-mapper: error adding target to table
 device-mapper: dm-linear: Device lookup failed
 device-mapper: error adding target to table
 device-mapper: dm-linear: Device lookup failed
 device-mapper: error adding target to table
 device-mapper: dm-linear: Device lookup failed
 device-mapper: error adding target to table
 device-mapper: dm-linear: Device lookup failed
 device-mapper: error adding target to table
 device-mapper: dm-linear: Device lookup failed
 device-mapper: error adding target to table
 device-mapper: dm-linear: Device lookup failed
 device-mapper: error adding target to table
 device-mapper: dm-linear: Device lookup failed
 device-mapper: error adding target to table
 NTFS driver 2.1.22 [Flags: R/O MODULE].
 Real Time Clock Driver v1.12
 input: PC Speaker
 inserting floppy driver for 2.6.10-ac12
 Floppy drive(s): fd0 is 1.44M
 FDC 0 is a post-1991 82077
 Linux agpgart interface v0.100 (c) Dave Jones
 agpgart: Detected NVIDIA nForce2 chipset
 agpgart: Maximum main memory to use for agp memory: 816M
 agpgart: AGP aperture is 64M @ 0xe0000000
 i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
 i2c_adapter i2c-1: nForce2 SMBus adapter at 0x2000
 usbcore: registered new driver usbfs
 usbcore: registered new driver hub
 ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
 ACPI: PCI Interrupt Link [LUBA] enabled at IRQ 5
 PCI: setting IRQ 5 as level-triggered
 ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 5 (level, low) -> IRQ 5
 ohci_hcd 0000:00:02.0: nVidia Corporation nForce2 USB Controller
 PCI: Setting latency timer of device 0000:00:02.0 to 64
 ohci_hcd 0000:00:02.0: irq 5, pci mem 0xe8003000
 ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
 hub 1-0:1.0: USB hub found
 hub 1-0:1.0: 3 ports detected
 ACPI: PCI Interrupt Link [LUBB] enabled at IRQ 10
 ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 10 (level, low) -> IRQ 10
 ohci_hcd 0000:00:02.1: nVidia Corporation nForce2 USB Controller (#2)
 PCI: Setting latency timer of device 0000:00:02.1 to 64
 ohci_hcd 0000:00:02.1: irq 10, pci mem 0xe8004000
 ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
 hub 2-0:1.0: USB hub found
 hub 2-0:1.0: 3 ports detected
 ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 11
 PCI: setting IRQ 11 as level-triggered
 ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 11 (level, low) -> IRQ 11
 ehci_hcd 0000:00:02.2: nVidia Corporation nForce2 USB Controller
 PCI: Setting latency timer of device 0000:00:02.2 to 64
 ehci_hcd 0000:00:02.2: irq 11, pci mem 0xe8005000
 ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
 PCI: cache line size of 64 is not supported by device 0000:00:02.2
 ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
 hub 3-0:1.0: USB hub found
 hub 3-0:1.0: 6 ports detected
 ACPI: PCI Interrupt Link [LACI] enabled at IRQ 9
 PCI: setting IRQ 9 as level-triggered
 ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 9 (level, low) -> IRQ 9
 PCI: Setting latency timer of device 0000:00:06.0 to 64
 intel8x0_measure_ac97_clock: measured 49964 usecs
 intel8x0: clocking to 47491
 cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
 pci_hotplug: PCI Hot Plug PCI Core version: 0.5
 shpchp: shpc_init : shpc_cap_offset == 0
 shpchp: shpc_init : shpc_cap_offset == 0
 shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
 Evaluate _OSC Set fails. Status = 0x0005
 pciehp: add_host_bridge: status 5
 pciehp: Fails to gain control of native hot-plug
 Evaluate _OSC Set fails. Status = 0x0005
 pciehp: add_host_bridge: status 5
 pciehp: Fails to gain control of native hot-plug
 ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
 ACPI: PCI interrupt 0000:01:08.0[A] -> GSI 11 (level, low) -> IRQ 11
 scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 6.2.36
         <Adaptec 2940 SCSI adapter>
         aic7870: Single Channel A, SCSI Id=7, 16/253 SCBs
   
 (scsi0:A:2): 8.064MB/s transfers (8.064MHz, offset 15)
   Vendor: iomega    Model: jaz 1GB           Rev: J^77
   Type:   Direct-Access                      ANSI SCSI revision: 02
 (scsi0:A:5): 8.064MB/s transfers (8.064MHz, offset 15)
   Vendor: SONY      Model: SDT-9000          Rev: 0601
   Type:   Sequential-Access                  ANSI SCSI revision: 02
 Attached scsi removable disk sda at scsi0, channel 0, id 2, lun 0
 st: Version 20041025, fixed bufsize 32768, s/g segs 256
 Attached scsi tape st0 at scsi0, channel 0, id 5, lun 0
 st0: try direct i/o: yes (alignment 512 B), max page reachable by HBA 1048575
 r8169 Gigabit Ethernet driver 1.2 loaded
 ACPI: PCI interrupt 0000:01:0b.0[A] -> GSI 11 (level, low) -> IRQ 11
 eth0: Identified chip type is 'RTL8169s/8110s'.
 eth0: RTL8169 at 0xf8b7e000, 00:0f:ea:38:1a:9e, IRQ 11
 ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
 ACPI: PCI interrupt 0000:01:0e.0[A] -> GSI 11 (level, low) -> IRQ 11
 ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[e7006000-e70067ff]  Max Packet=[2048]
 NET: Registered protocol family 17
 ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea0000358a00]
 r8169: eth0: link up
 NET: Registered protocol family 10
 Disabled Privacy Extensions on device c02ed300(lo)
 IPv6 over IPv4 tunneling driver
 ACPI: Power Button (FF) [PWRF]
 ibm_acpi: acpi_evalf(DHKC, d, ...) failed: 4097
 ibm_acpi: `enable,0xffff' invalid for parameter `hotkey'
 toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
 apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
 apm: overridden by ACPI.
 Device not ready.  Make sure there is a disc in the drive.
 eth0: no IPv6 routers present

 ------- ls /dev/hd* ---------

/dev/hda   /dev/hda5  /dev/hdb2  /dev/hdd   /dev/hdf   /dev/hdg1
 /dev/hda1  /dev/hdb   /dev/hdb5  /dev/hde   /dev/hdf1
 /dev/hda2  /dev/hdb1  /dev/hdc   /dev/hde1  /dev/hdg

---

### Post by keikoz on 2005-07-18
Humm that's really strange: in that case, it seems you didnt need to use the patch, maybee; the dmesg of your warty-startup indicates that your cd-rom/dvd are recognized; you maybee even didnt need to use the patch and recompile all that :p

Watch the first dmesg you gave me: the cd/dvd is there; and the ls /dev/hd* gives you the right devices; so try starting on warty, and mount your cd like i told you: put a cd in your hde drive, and :

mount -t iso9660 /dev/hde /media/cdrom

(the /media/cdrom should exist before you do that; if it doesnt, create it yourself like this:

mkdir /media/cdrom

I watch your second dmesg and seems you have the same pbl i have: a problem with drive allocation: your Hard disks are listed as hde/hdf, and that isnt normal...

keikoz

---

### Post by man_exec on 2005-07-18
keikoz,

it's not my cdroms that I have trouble with.  
 
I've got 3 ide drives on the ITE8212 controller.
 
/hde
/hdf
/hdg
 
I've got 2 ide drives on the main ide controller
 
/hda
/hdb
 
In the Warty kernel, I can't see the ITE8212 controller or the drives, but I can see and access the primary ide controller & drives.  In the ac-12 kernel, I can 'see' all ide drives with 'cfdisk'.  However, I can't access them at all. 
 
I suspect that this has something to do with IRQ sharing, although that is just a guess.  Any ideas?
 
arvan

---

### Post by keikoz on 2005-07-18
Ok sorry, i did not exactly understand then...

I too suspect something with the IRQ; or another idea: i read somewhere (where?) that there is a bug with the hotplug system in debians-distribution; probably the ubuntu kernel is patched against that problem, but the standard kernel isn't... that could explain the conflicts we have on the ide-controllers...

my problem is a little bit different:the drives are strangely allocated: the ITE8212 is token as main IDE, and nothing works because the primary HD becomes /dev/hde, and the atapi devices are read as hda and hdb ...

...

life's hard ...

keikoz

---

