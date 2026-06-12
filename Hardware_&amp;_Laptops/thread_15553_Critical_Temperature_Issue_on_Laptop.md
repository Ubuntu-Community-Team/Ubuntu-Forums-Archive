---
title: "Critical Temperature Issue on Laptop"
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by mhancoc7 on 2005-02-15
Hi,
I am dual booting XP and Ubuntu on my Compaq Armada 1750. I am having trouble with overheating. I get the Critical Temperature warning and then the laptop shuts down. The fan works fine in XP, but is sort of random in Ubuntu. Sometimes it works fine and others not at all. I have noticed that if I reboot after a Critical Temperature shutdown the fan will come on at boot up and usually work fine in Ubuntu thereafter. Could someone give this Linux newbie some easy to follow guidance on possible solutions to this issue.

Thanks in advance, Jereme :)

---

### Post by Harderlump on 2005-02-15
Maybe you could use APM instead of ACPI.
See [http://ubuntulinux.org/wiki/SuspendHowto](http://ubuntulinux.org/wiki/SuspendHowto)

---

### Post by mhancoc7 on 2005-02-15
Thanks for the help.
I followed the instructions that you pointed me to. Everything boots up fine. I still get the synaptics fail error message, but  now I don't get the errors associated with the shpchp and pciehp that I was getting before. However the laptop is still random about when the fan will work or not. I would rather the fan run constantly than this. I don't know how the repeated overheating will affect the lifespan of the laptop, but it can't be good. Do you know of anything else that I could try.
Thanks, Jereme

---

### Post by Harderlump on 2005-02-16
Hmm, I'm do not know very much about that. It's only that my Thinkpad works better with APM,
and sometimes I hear from other people about problems with ACPI.
With APM you have less control than with ACPI, and I wonder if the fan is
under APM control. I believe with APM it leaves that to the BIOS (however, I'm not sure).
So, are you sure, it runs APM now (try lsmod, look for apm or acpi)?
Have you checked the "Power Management" settings in the BIOS?

---

### Post by mhancoc7 on 2005-02-16
Well I have done a fresh install with acpi=on. I tried the lsmod and here are the results:

> Module                  Size  Used by
nls_iso8859_1           4352  1
nls_cp437               6016  1
vfat                   13312  1
fat                    41792  1 vfat
sd_mod                 20480  2
usb_storage            59200  1
scsi_mod              115148  2 sd_mod,usb_storage
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ipv6                  230020  8
ds                     17796  4
button                  6936  0
ac                      5132  0
battery                 9740  0
yenta_socket           19328  0
pcmcia_core            63156  2 ds,yenta_socket
uhci_hcd               29328  0
usbcore               104292  4 usb_storage,uhci_hcd
intel_agp              20512  1
agpgart                31784  1 intel_agp
rtc                    12216  0
pcspkr                  3816  0
floppy                 54996  0
irtty_sir               8320  0
sir_dev                18092  1 irtty_sir
irda                  167360  2 irtty_sir,sir_dev
crc_ccitt               2432  1 irda
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
tsdev                   7168  0
parport                37320  2 parport_pc,lp
evdev                   9088  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   25904  680
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb


I do not see apm or acpi listed. I do see the fan listed. Oddly enough the laptop is running well today. So far the fan has been coming on fine. I still am not sure though that I have it running right.

Thanks, Jereme

---

### Post by Harderlump on 2005-02-16
You are right, I cannot see the acpi module, too (also on my computer).
But it looks more like ACPI from the module list.

Better check the output of dmesg to see the startup messages of each module.

You should also look here:
  [http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops)

Your machine is not on that list, but you'll find some hints there.

I hope that helps :-)

---

### Post by mhancoc7 on 2005-02-16
Here is the output from dmesg:

> mhancoc7@ubuntulaptop:~ $ dmesg
Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 12:41:57 BST 2004
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000000bff8000 (usable)
 BIOS-e820: 000000000bff8000 - 000000000c000000 (ACPI NVS)
191MB LOWMEM available.
On node 0 totalpages: 49144
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 45048 pages, LIFO batch:10
  HighMem zone: 0 pages, LIFO batch:1
DMI not present.
ACPI: RSDP (v000 COMPAQ                                ) @ 0x000fb2a0
ACPI: RSDT (v001 COMPAQ RSDTBL   0x00000001 CPQ  0x00000001) @ 0x0bff8000
ACPI: FADT (v001 COMPAQ CPQB142  0x19991130 CPQ  0x00000001) @ 0x0bff8028
ACPI: DSDT (v001 COMPAQ ARMADA17 0x00010000 MSFT 0x0100000a) @ 0x00000000
ACPI: PM-Timer IO Port: 0xf08
Built 1 zonelists
Kernel command line: root=/dev/hda2 ro acpi=on quiet splash
Local APIC disabled by BIOS -- reenabling.
Could not enable APIC!
Initializing CPU#0
PID hash table entries: 1024 (order 10: 8192 bytes)
Detected 497.767 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 187580k/196576k available (1336k kernel code, 8372k reserved, 728k data, 204k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 987.13 BogoMIPS
Security Scaffold v1.0.0 initialized
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000
CPU: After vendor identify, caps:  0387f9ff 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU serial number disabled.
CPU: After all inits, caps:        0383f9ff 00000000 00000000 00000040
CPU: Intel Pentium III (Coppermine) stepping 01
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: IRQ9 SCI: Edge set to Level Trigger.
checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Freeing initrd memory: 4116k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xf0484, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20040816
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [C000] (00:00)
PCI: Probing PCI hardware (bus 00)
ACPI: PCI Interrupt Routing Table [\_SB_.C000._PRT]
ACPI: PCI Interrupt Link [C0F2] (IRQs *11)
ACPI: PCI Interrupt Link [C0F6] (IRQs *11)
ACPI: Power Resource [C103] (on)
ACPI: Power Resource [C105] (on)
Linux Plug and Play Support v0.97 (c) Adam Belay
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00fe2d0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x4d38, dseg 0xf0000
PnPBIOS: 19 nodes reported by PnP BIOS; 19 recorded by driver
PCI: Using ACPI for IRQ routing
ACPI: PCI Interrupt Link [C0F6] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI Interrupt Link [C0F2] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:11.0[A] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI interrupt 0000:00:11.1[A] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 11 (level, low) -> IRQ 11
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Limiting direct PCI/PCI transfers.
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 2
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 1024 buckets, 8Kbytes
TCP: Hash tables configured (established 16384 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
ACPI: (supports S0 S3 S4 S4bios S5)
ACPI wakeup devices:
C059 C05A
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4116 blocks [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 204k freed
vesafb: probe of vesafb0 failed with error -6
ACPI: Processor [C098] (supports C1 C2, 8 throttling states)
ACPI: Thermal Zone [C106] (59 C)
ACPI: Fan [C102] (on)
ACPI: Fan [C104] (on)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
PIIX4: IDE controller at PCI slot 0000:00:07.1
PIIX4: chipset revision 1
PIIX4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x2020-0x2027, BIOS settings: hda:DMA, hdb:DMA
hda: TOSHIBA MK6411MAT, ATA DISK drive
hdb: TOSHIBA CD-ROM XM-1802B, ATAPI CD/DVD-ROM drive
Using anticipatory io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 12685680 sectors (6495 MB), CHS=13424/15/63, UDMA(33)
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
ide2: I/O resource 0x3EE-0x3EE not free.
ide2: ports already in use, skipping probe
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 120920k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda2, internal journal
synaptics reset failed
synaptics reset failed
synaptics reset failed
Unable to query Synaptics hardware.
input: PS/2 Synaptics TouchPad on isa0060/serio1
mice: PS/2 mouse device common for all mice
hdb: ATAPI 24X CD-ROM drive, 128kB Cache, DMA
Uniform CD-ROM driver Revision: 3.20
ts: Compaq touchscreen protocol output
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
lp0: using parport0 (interrupt-driven).
Capability LSM initialized
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
hdb: packet command error: error=0x50
cdrom: open failed.
irda_init()
NET: Registered protocol family 23
inserting floppy driver for 2.6.8.1-3-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
input: PC Speaker
Real Time Clock Driver v1.12
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 440BX Chipset.
agpgart: Maximum main memory to use for agp memory: 149M
agpgart: AGP aperture is 64M @ 0x44000000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:07.2: Intel Corp. 82371AB/EB/MB PIIX4 USB
uhci_hcd 0000:00:07.2: irq 11, io base 00002000
uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:00:11.0[A] -> GSI 11 (level, low) -> IRQ 11
Yenta: CardBus bridge found at 0000:00:11.0 [0e11:b121]
Yenta: Enabling burst memory read transactions
Yenta: Using CSCINT to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:00:11.0, mfunc 0x01001c72, devctl 0x64
Yenta: ISA IRQ mask 0x0418, PCI irq 11
Socket status: 30000006
ACPI: PCI interrupt 0000:00:11.1[A] -> GSI 11 (level, low) -> IRQ 11
Yenta: CardBus bridge found at 0000:00:11.1 [0e11:b121]
Yenta: Using CSCINT to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:00:11.1, mfunc 0x01001c72, devctl 0x64
Yenta: ISA IRQ mask 0x0418, PCI irq 11
Socket status: 30000006
ACPI: Battery Slot [C0D6] (battery present)
ACPI: Battery Slot [C0D7] (battery absent)
ACPI: AC Adapter [C0CC] (on-line)
ACPI: Lid Switch [C108]
ACPI: Sleep Button (CM) [C059]
ACPI: Power Button (CM) [C05A]
cs: IO port probe 0x0100-0x04ff: excluding 0x100-0x107 0x220-0x22f 0x250-0x257 0x260-0x267 0x330-0x337 0x388-0x38f 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02cc0c0(lo)
IPv6 over IPv4 tunneling driver
psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
mhancoc7@ubuntulaptop:~ $


I see ACPI mentioned a lot. Do you see anything here that may be causeing the issue. I am a newbie so I have no idea. I also saw where it says Could not enable APCI. What is that?

Thanks so much for your assistance.
Jereme

---

### Post by Harderlump on 2005-02-16
There are many people having trouble with power management in Linux.
With my Thinkpad R40 it seems that I have suspend (to RAM) using APM, and
I could have hibernate (=suspend too disk) with ACPI, but not both at atime.
I decided to take APM, because suspend is more important for me.

So, since APM and ACPI are so different, it may solve your problem, too.
Just give it a try!

In Ubuntu, ACPI is enabled by default.

To enable APM, just edit your /boot/grub/menu.lst. Add "apm=on acpi=off noacpi" to 
your kernel line of the booting kernel.
Or just edit the kopt line (see below), and call update-grub (so it puts the options on
every existing and future kernel line)
# kopt=root=/dev/hda8 ro apm=on acpi=off noacpi

Reboot, and look for dmesg, and check lsmod for the apm kernel module.

Then APM is active, and ACPI is down, and hopefuly your fan is doing a good job...

---

### Post by mhancoc7 on 2005-02-16
Thanks for the tip, still no go though. I have tried every combination of turning off acpi and apm that I can find on the forum. I also added apm to the /etc/modules file manually, but I am still getting the overheating. Is there a way that I can force the fan on. Or better yet is there a way to change what temp will trigger the fan. Of is there something else I can try that you are aware of.

I tried to turn ACPI off in BIOS by using my setup disk, but when I try to log into WinXP from the grub menu with ACPI off the laptop hangs on a blank screen.

Thanks, Jereme

---

### Post by mhancoc7 on 2005-02-16
Ok, I think I have got it solved.

I put acpi=force and pci=noacpi on the # kopt line in /boot/grub/menu.lst file. I then ran sudo update grub. Then rebooted.

Now the fan works fine with one exception. If I restart the laptop using the Top Panel (Computer > Log Out > Restart). The fan does not work. If shut down the laptop from the Top Panel (Computer > Log Out > Shutdown) the fan works fine the next time I start the laptop. I can also do a sudo reboot and the fan will work fine on reboot. 

Thank you so much for your help. I really appreciate it. I am new to linux and I really like Ubuntu so far. Now I just need to get my modem working and I will be set.

God Bless, Jereme

---

### Post by mhancoc7 on 2005-02-17
Ok, I spoke too soon. I booted up my laptop this morning and let it sit for about 15 minutes. It finally reached a Critical Temp and shut down. I rebooted and the fan came on and booted into Ubuntu just fine with the fan running. Apparently the only way to get the fan to come on in Ubuntu is to get the laptop to a Critical Temp and then reboot. It seems that if the laptop is hot the fan comes on, but if the laptop is cool the fan will not kick on once it gets hot. This is really starting to discourage me.

Thanks, Jereme

---

### Post by mhancoc7 on 2005-02-17
Ok, Now I think I have finally found the answer to my problem. I did a google search and found a way to force the fan to stay on. This is not me ideal solution, but at least I should not have the Critical Temp issue anymore. Another downside is that I lose my battery indicator, etc, but that is not that big of a deal to me. 

The solution:

add noacpi apm=off acpi=off no-hlt to #kopt line and sudo update-grub

Now the fan is forced to stay on.

Thanks, Jereme

---

