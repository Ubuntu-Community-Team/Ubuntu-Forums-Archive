---
title: "Battery Charge meter not working"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by cnayak on 2005-08-05
I have an Acer Travelmate 2300 series laptop. I enabled the battery charge meter in the gnome panel , but it gives the following message:

   System is currently running on battery power, battery status unknown

    even when I use an  ac outlet, it gives th same message.

 How do I fix this problem?

 Regards,
 Chandan

---

### Post by luca_linux on 2005-08-05
Do you get any error in dmesg? (Just type dmesg to see that).
Anyway, maybe you have a Smart Battery and you need this: [https://sourceforge.net/projects/sbs-linux/](https://sourceforge.net/projects/sbs-linux/)
Before installing, make sure you have a smart battery by looking at device list.

---

### Post by cnayak on 2005-08-05
**This is the output I get. Can't figure out anything, though.**

Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
 BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
 BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001eee0000 (usable)
 BIOS-e820: 000000001eee0000 - 000000001eeec000 (ACPI data)
 BIOS-e820: 000000001eeec000 - 000000001ef00000 (ACPI NVS)
 BIOS-e820: 000000001ef00000 - 0000000020000000 (reserved)
 BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
 BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
 BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
494MB LOWMEM available.
On node 0 totalpages: 126688
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 122592 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI present.
ACPI: RSDP (v000 ACER                                  ) @ 0x000f62e0
ACPI: RSDT (v001 ACER   Kestrel  0x20021228  LTP 0x00000000) @ 0x1eee7ba8
ACPI: FADT (v001 ACER   Kestrel  0x20021228 PTL  0x00000050) @ 0x1eeebf2c
ACPI: HPET (v001 ACER   Kestrel  0x20021228 PTL  0x00000000) @ 0x1eeebfa0
ACPI: BOOT (v001 ACER   Kestrel  0x20021228  LTP 0x00000001) @ 0x1eeebfd8
ACPI: DSDT (v001 ACER   Kestrel  0x20021228 MSFT 0x0100000e) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
ACPI: HPET id: 0x8086a201 base: 0x0
Built 1 zonelists
Kernel command line: root=/dev/hda7 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (013e4000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1298.897 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 494876k/506752k available (1436k kernel code, 11292k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 2572.28 BogoMIPS (lpj=1286144)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: afe9f9bf 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 1024K
CPU: After all inits, caps: afe9f9bf 00000000 00000000 00000040 00000000 00000000
CPU: Intel(R) Celeron(R) M processor         1.30GHz stepping 06
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0440)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd792, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
ACPI: Embedded Controller [EC0] (gpe 29)
ACPI: Power Resource [PFN0] (off)
ACPI: Power Resource [PFN1] (off)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 7 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:03: ioport range 0x164e-0x164f has been reserved
Simple Boot Flag at 0x37 set to 0x1
audit: initializing netlink socket (disabled)
audit(1123299685.421:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 10 (level, low) -> IRQ 10
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
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
GLAN MPCI T394 MDM0 USB1 USB2 USB3
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Fan [FAN0] (off)
ACPI: Fan [FAN1] (off)
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [THRM] (52 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
PCI: setting IRQ 6 as level-triggered
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 6 (level, low) -> IRQ 6
ICH4: chipset revision 3
ICH4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: ST94019A, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 p7 >
Probing IDE interface ide1...
hdc: UJDA760 DVD/CDRW, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (455 pages freed)
Restarting tasks... done
Adding 1052216k swap on /dev/hda6.  Priority:-1 extents:1
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
 Firmware: 5.9
 Sensor: 18
 new absolute packet format
 Touchpad has extended capability bits
 -> 4 multi-buttons, i.e. besides standard buttons
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio4
Capability LSM initialized
ts: Compaq touchscreen protocol output
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS volume version 3.1.
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Real Time Clock Driver v1.12
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 855 Chipset.
agpgart: Maximum main memory to use for agp memory: 423M
agpgart: Detected 16252K stolen memory.
agpgart: AGP aperture is 128M @ 0xe8000000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 6 (level, low) -> IRQ 6
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 6, io base 0x1820
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 6 (level, low) -> IRQ 6
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 6, io base 0x1840
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 6 (level, low) -> IRQ 6
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 6, io base 0x1860
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 2-1: new low speed USB device using uhci_hcd and address 2
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 10 (level, low) -> IRQ 10
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 10, pci mem 0xe0100000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
usb 2-1: USB disconnect, address 2
usbcore: registered new driver hiddev
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
usb 2-1: new low speed USB device using uhci_hcd and address 3
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1
hw_random: cannot enable RNG, aborting
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49880 usecs
intel8x0: clocking to 48000
b44.c:v0.95 (Aug 3, 2004)
ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 6 (level, low) -> IRQ 6
eth0: Broadcom 4400 10/100BaseT Ethernet 00:c0:9f:76:d5:6d
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Enabling device 0000:02:06.0 (0104 -> 0106)
ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 10 (level, low) -> IRQ 10
Yenta: CardBus bridge found at 0000:02:06.0 [1025:0064]
Yenta: ISA IRQ mask 0x08b8, PCI irq 10
Socket status: 30000006
b44: eth0: Link is down.
b44: eth0: Link is up at 100 Mbps, full duplex.
b44: eth0: Flow control is on for TX and on for RX.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
apm: BIOS not found.
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 6 (level, low) -> IRQ 6
[drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corp. 82852/855GM Integrated Graphics Device
[drm] Initialized i915 1.2.0 20040405 on minor 1: Intel Corp. 82852/855GM Integrated Graphics Device (#2)
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: excluding 0x800-0x807
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: no IPv6 routers present
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A

---

### Post by luca_linux on 2005-08-06
It seems there's no error. Anyway, read the readme file coming with sbs (the driver I linked in the post above) and see if your laptop is included among the reported ones.

---

### Post by briguy on 2005-08-07
Check this post: [http://www.ubuntuforums.org/showthread.php?t=49045](http://www.ubuntuforums.org/showthread.php?t=49045)

---

### Post by AdeptPaladin on 2005-08-07
I have a similar version of Acer (2303LCi)... and after much trials, managed to get IASL compiled and installed (found a binary version after I couldn't compile the file; installed Bison, gcc, and Flex-Old and it still spat out error messages.).

I now have patched and fixed up the dsdl.dat that the readme says to use.  However, when I type in 
```
iasl dsd.dsl
``` 
I get:
```
Intel ACPI Component Architecture
ASL Optimizing Compiler / AML Disassembler version 20040715 [Sep 22 2004]
Copyright (C) 2000 - 2004 Intel Corporation
Supports ACPI Specification Revision 2.0c

dsdt.dsl  3664: INCLUDE ("smbus-cm.asl")
Error    1009 -                       ^ Could not open include file (smbu s-cm.asl (No such file or directory))

dsdt.dsl  3666: INCLUDE ("sbs-cm-1b.asl")
Error    1009 -                        ^ Could not open include file (sbs -cm-1b.asl (No such file or directory))

dsdt.dsl  3669: }
Error    1037 - ^ syntax error, unexpected '}'

ASL Input:  dsdt.dsl - 3672 lines, 123563 bytes, 1708 keywords
Compilation complete. 3 Errors, 0 Warnings, 0 Remarks, 0 Optimizations
```
And no dsdt.aml file that I can find.  O_o

Help?


EDIT:

Ok, I fixed that (I forgot to extract the files needed) but now, I can't figure out how to get Grub to load the DSDT.aml file.

```
title		Ubuntu, kernel 2.6.10-5-686
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot
```
That's the default entry I have, so far all I've done is put the DSDT.aml file into the folder listed.  But that didn't seem to work.  Furthermore, how can I check to see if it's working?  Would cat /proc/acpi/battery show something other than 'this is a directory' ?

---

### Post by luca_linux on 2005-08-07
```

echo -n "INITRDDSDT123DSDT123" >> /boot/initrd.img-{version}-dsdt
cat DSDT.aml >> /boot/initrd.img-{version}-dsdt
echo -n "INITRDDSDT321DSDT321" >> /boot/initrd.img-{version}-dsdt

```

Anyway, have a look at this site: [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)

---

### Post by briguy on 2005-08-08
You have to re-setup the initrd every time the kernel changes, so it's useful to have a script to update it when this happens.  Here's what I put together for my laptop:

echo "processing mkinitrd..."
mkinitrd -o /boot/initrd.img-`uname -r`
echo "adding INITRDDSDT to initrd.img"
echo -n "INITRDDSDT123DSDT123" >> /boot/initrd.img-`uname -r`
echo "adding DSDT.aml to initrd.img"
cat DSDT.aml >> /boot/initrd.img-`uname -r`
echo "done"

---

### Post by AdeptPaladin on 2005-08-08
Ok, got the DSDT.aml added... however, it seems I need the initramfs patch as well.  When I go to install it, there's two problems:

1) I don't have a /usr/src/linux (I have a /usr/src/linux-2.6.10-5-686 though, which is essentially the same thing, right?)

2) Secondly, it asks which file I want to patch... but the site doesn't say what you need to. In fact, the site's extremely lacking on details and there's no readme at all.  Argh, I'm so close I can taste it!


Other good news, managed to get ndiswrapper to properly work with my WLAN card (IPN2220); I had to pretty much uninstall the old version and then install the latest from Sourceforge (1.2).  The previous one worked but wouldn't associate with my access point.  However, now it does.    XMMS used to hang when I went to play an mp3.  The solution was changing the plugin from OSS to ESD.  Then viola!

Things left to fix:

1) Smart-battery support/detection (which it seems I've almost completed)
2) Finding out how to get the ACPI/powernowd to work with my Celeron M processor and how to control my LCD screen's brightness.

---

### Post by luca_linux on 2005-08-08
The official Ubuntu kernel is already patched.

---

### Post by AdeptPaladin on 2005-08-08
[QUOTE=luca_linux]The official Ubuntu kernel is already patched.[/QUOTE]
Then why do I get this error:
"kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (0,0)"
... which is the exact same as the error as if initramfs wasn't patched?

I'm confused now.

---

### Post by Mo.Bang on 2005-11-01
Hi,

did you solve the kernel panic?
I'm in the same situation on breezy.

Ralf

---

### Post by Mo.Bang on 2005-11-01
Ok, I solved my Problem.

It was the mkinitramfs thing.
Just copy DSDT.aml to /etc/mkinitramfs
execute as root mkinitramfs -o <filename>
copy the <filename> to /boot and add it in /boot/grub/menu.lst
after the initrd=

So your original is save and the new one includes the dsdt.

Check after reboot with cat /var/log/syslog | grep DSDT

Good Night

Ralf

---

### Post by spade_shark on 2005-11-06
I have similar issue?  Running 5.1.  Gateway solo laptop series.  It appears to have 10 hours of battery life :smile: .  Ah if only it were true.  Meter shows power plug as unit is charging, once 100% charged...changes to battery icon and says system is running on battery and 10 hours remaining.  Battery life seems very similar to "normal" run time however (2.5 hrs).  Appears to be cosmetic only.  Fans run more often and laptop runs warmer, however I have higher cpu loads then say standard XP system.

---

