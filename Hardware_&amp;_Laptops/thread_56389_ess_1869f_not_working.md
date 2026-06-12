---
title: "ess 1869f not working"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by novaflash on 2005-08-12
Hi. I'm a total stranger to the world of linux. I tried running Ubuntu and am fairly surprised at how everything's going so far. I have one problem though.

I have a compaq deskpro pentium II 350mhz computer with 128mb ram, 4gb harddrive and onboard audio and ethernet. The videocard and ethernet stuff are all detected and working properly. However, the soundchip was not detected. I found out that apparently ubuntu uses ALSA to get sound in the GUI. I looked on their website and found that the module snd-es18xx should work on my ess es1869f chip. I read also that I should try a modprobe snd-es18xx from the root shell. This is the result;

FATAL: Error inserting snd_es18xx (/lib/modules/2.6.10-5-386/kernel/sound/isa/snd-es18xx.ko): no such device
FATAL: Error running install command for snd_es18xx

Does anyone have any suggestion? Googling didn't quite help me here. Remember, I'm a complete n00b to linux, but not to computers. I opened the case and found the chip there, and it's enabled in the bios. It ought to work. ps; knoppix livecd DOES find my sound and it DOES work.


edit:
Audio device in bios says:
220-22F,
388-38B,
330-331,
IRQ 5,
DMA 1,
DMA 0

---

### Post by wvslkr on 2005-08-12
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

---

### Post by novaflash on 2005-08-12
Yes thank you, I know how google works as well.

Unfortunately none of the suggestions there do anything for me.

**root@UBUNTU:/ # modprobe snd-es18xx**
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.10-5-386/kernel/sound/isa/snd-es18xx.ko): no such device
FATAL: Erorr running install command for snd_es18xx

**root@UBUNTU:/ # alsamixer**
alsamixer: function snd_ctl_open failed for default: No such device

Any more ideas?

---

### Post by wvslkr on 2005-08-12
Try   modprobe snd-es18xx isapnp=0

If that doesn't work you may want to look at this thread if you haven't done so [http://www.ubuntuforums.org/showthread.php?t=12525&highlight=es1869](http://www.ubuntuforums.org/showthread.php?t=12525&highlight=es1869)

GL

---

### Post by novaflash on 2005-08-13
[QUOTE=wvslkr]Try   modprobe snd-es18xx isapnp=0

If that doesn't work you may want to look at this thread if you haven't done so [http://www.ubuntuforums.org/showthread.php?t=12525&highlight=es1869](http://www.ubuntuforums.org/showthread.php?t=12525&highlight=es1869)

GL[/QUOTE]


Mmm, the first suggestion gave me the exact same error messages I've been getting all along:
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.10-5-386/kernel/sound/isa/snd-es18xx.ko)
FATAL: Error running install command for snd_es18xx

I looked at the thread and tried various things.

I added
acpi_irq_isa=5
to #kopt
in the
/boot/grub/menu.lst

I edited /etc/modules file to include
snd-es1869

I also tried snd-es18xx instead.

alsaconf gives me a command not found error, and trying to locate the file didn't give me any results. However, alsamixer was installed and gave me the following response:

alsamixer: function snd_ctl_open failed for default: no such device

I also followed a wild suggestion and typed in lsmod|grep snd and got this:
snd_pcm_oss          47652  0
snd_mixer_oss        16768  1 snd_pcm_oss
snd_pcm                 84872  1 snd_pcm_oss
snd_page_alloc        9604  1 snd_pcm
snd_opl3_lib         10112  0
snd_timer          23300  2 snd_pcm,snd_opl3_lib
snd_hwdep          9220  1 snd_opl3_lib
snd_mpu401_uart      7168  0
snd_rawmidi             22944  1 snd_mpu401_uart
snd_seq_device        8332  2 snd_opl3_lib,snd_rawmidi
snd                            50276  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore                9824  1 snd

I have no clue what this does or what this means.

Trying to run alsacnt in root terminal gave me command not found.

I also tried saving the following lines in the file /etc/modprobe.d/soundcard
alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

But that didn't work. Also tried the secondary suggestion:
alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1

And that didn't work either. Cause when I then tried to run the commands:
sudo modprobe snd-es18xx
sudo /etc/init.d/alsa restart

The first command would give me that same device not found fatal error like i've stated so many times before, and the second one would just go into a loop where it would state "soundcard not found" then give a beep, show a lot of helptext in the console, and would state "soundcard not found" then give a beep, etc..etc.. ad infinitum, until I hit ctrl+z to get out of this loop.

Also, whenever I do a modprobe snd-es18xx and shut the machine down, it starts beeping a lot and very quickly I can see "invalid card number". It does this about 17 times, then it finally shuts down. After a reboot or two it does eventually go away again. I have no clue as to what's going on or how to resolve it.

I also tried editing etc/modules and adding the line snd-es18xx isapnp=0 but that didn't resolve the problem either.

I wonder though, I read in some post that perhaps the solution is in bios settings? Because in the bios I have the option of setting the Onboard Device AUDIO DEVICE to either of these two options:
 220x22F, 388-38B, 330,331, IRQ 5, DMA 1, DMA 0
  or
 DISABLED

And I also have the option to set the IRQ's for Onboard Ethernet controller, VGA controller, Unknown device (which i presume is the pci to isa bridge for the onboard soundchip, but am unsure of this..) and the USB controller. I've tried to set them up so they had no conflicting irq's. Most everything seems to work except the soundcard.

Still clueless.

---

### Post by wvslkr on 2005-08-13
Phew, it looks like you have been through the whole ball of knots.  I agree with you that you probably have a conflict somewhere, or because of the isa bridge.  

The only other suggestions I have are run dmesg in a term and see if you can see an error that may send you in the right direction.  You say it worked under Knoppix; try  copying the settings from it and see if they work.  

You have more patience than I.  I would probably have disabled it and stuck in another card by now.  

Good Luck :)

---

### Post by novaflash on 2005-08-14
I'll try the dmesg command... i've pasted the results below.

So, in your opinion, there's not much more a user can do to try and get his card to work under ubuntu? It seems to me I need the help of someone that has actually worked on this system - like someone from alsa or ubuntu. It seems to me people like that don't visit these forums. Perhaps I'll have to try usenet.

Oh, and, I don't know the settings knoppix used. Any way to figure out, except go through every file mentioned in previous posts and writing everything down? :-/

Oh well

root@ubuntu:/home/gebruiker # dmesg
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000008000000 (usable)
 BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
128MB LOWMEM available.
On node 0 totalpages: 32768
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 28672 pages, LIFO batch:7
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.1 present.
ACPI: RSDP (v000 COMPAQ                                ) @ 0x000e0010
ACPI: RSDT (v001 COMPAQ INDY     0x00000001  0x00000000) @ 0x000e0080
ACPI: FADT (v001 COMPAQ INDY     0x00000001  0x00000000) @ 0x000e00cc
ACPI: SSDT (v001 COMPAQ VILLTBL1 0x00000001 MSFT 0x01000004) @ 0x000e09c3
ACPI: SSDT (v001 COMPAQ PNP_PRSS 0x00000001 MSFT 0x01000004) @ 0x000e1a6e
ACPI: DSDT (v001 COMPAQ     DSDT 0x00000001 MSFT 0x01000004) @ 0x00000000
ACPI: PM-Timer IO Port: 0xf808
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01102000)
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 16384 bytes)
Detected 348.274 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 122396k/131072k available (1436k kernel code, 8132k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 688.12 BogoMIPS (lpj=344064)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 512K
CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000
CPU: Intel Pentium II (Deschutes) stepping 02
Enabling fast FPU save and restore... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0a00)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xed8eb, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *9
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11)
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
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
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:0c: ioport range 0x15c-0x15d has been reserved
pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:0d: ioport range 0xf800-0xf81f could not be reserved
pnp: 00:0d: ioport range 0xf820-0xf83f has been reserved
pnp: 00:0d: ioport range 0xfc00-0xfc0f has been reserved
audit: initializing netlink socket (disabled)
audit(1124010290.179:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Limiting direct PCI/PCI transfers.
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
PCI: Enabling device 0000:00:0e.0 (0084 -> 0087)
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:0e.0[A] -> GSI 11 (level, low) -> IRQ 11
ttyS15 at I/O 0x2408 (irq = 11) is a 16450
ttyS50 at I/O 0x2410 (irq = 11) is a 8250
ttyS51 at I/O 0x2418 (irq = 11) is a 16450
ttyS52 at I/O 0x2420 (irq = 11) is a 8250
ttyS53 at I/O 0x2428 (irq = 11) is a 8250
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
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
IP: routing cache hash table of 1024 buckets, 8Kbytes
TCP: Hash tables configured (established 8192 bind 16384)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0  RTC PS2M  KBD COM1 COM2 USB0 PBTN
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: CPU0 (power states: C1[C1] C2[C2])
ACPI: Processor [CPU0] (supports 8 throttling states)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
PIIX4: IDE controller at PCI slot 0000:00:14.1
PIIX4: chipset revision 1
PIIX4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x2040-0x2047, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x2048-0x204f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: WDC AC14300R, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 8421840 sectors (4311 MB) w/512KiB Cache, CHS=8912/15/63, UDMA(33)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
hdc: COMPAQ CD-ROM CDRU241, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (455 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 208804k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 24X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a National Semiconductor PC87306
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 440BX Chipset.
agpgart: Maximum main memory to use for agp memory: 96M
agpgart: AGP aperture is 64M @ 0x44000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
e100: Intel(R) PRO/100 Network Driver, 3.2.3-k2-NAPI
e100: Copyright(c) 1999-2004 Intel Corporation
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 11 (level, low) -> IRQ 11
e100: eth0: e100_probe: addr 0x40200000, irq 11, MAC addr 00:50:8B:34:5A:94
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:14.2[D] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:14.2: Intel Corp. 82371AB/EB/MB PIIX4 USB
NET: Registered protocol family 17
uhci_hcd 0000:00:14.2: irq 11, io base 0x2020
uhci_hcd 0000:00:14.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
piix4_smbus 0000:00:14.3: Found 0000:00:14.3 device
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (CM) [PBTN]
ibm_acpi: ec object not found
eth0: no IPv6 routers present
apm: BIOS not found.
ibm_acpi: ec object not found
root@ubuntu:/home/gebruiker #

---

### Post by wvslkr on 2005-08-14
There is always more that can be done if the patience lasts.  Yes from Knoppix you would have to hunt up the relevent entries.

I looked through dmesg and noticed that you seem to be using acpi while I am not if I am understanding correctly.  Attached, my dmesg for comparison.  Note that yours also seems to complain about something in the initrd also. Related I don't know.

Suggest trying passing the no acpi argument to the kernel when you boot and try modprobe then.  Thinking conflict between bios pnp and acpi.  If modprobe works you will still need to add snd-es18xx isapnp=0 to /etc/modules to make permanent.  My chip isn't recognised on setup but is just a modprobe and go.

Again Good Luck :)

---

