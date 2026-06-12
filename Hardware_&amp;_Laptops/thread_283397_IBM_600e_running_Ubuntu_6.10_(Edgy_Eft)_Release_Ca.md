---
title: "IBM 600e running Ubuntu 6.10 (Edgy Eft) Release Candidate"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by clembone on 2006-10-24
Hello all. Well I have been running Ubuntu for a couple of days now and I must say it is a nice OS. :KS

I have rebuilt my IBM 600e about 5 times switching between 6.06 and 6.10. It seems that 6.10 is more stable than 6.06 and I will probably run 6.10 going forward.

I, like many others on this site, ran into the sound issue on the 600e which I was able to overcome in the 6.06 release. I have not had the same fortune with 6.10. It seems to be that I cannot disable the PNP portion of 6.10 and thus the wrong driver is loaded. Can anyone assist me on this? 

Here is a link to my post on how I fixed my sound on the 600e running 6.06. 

[http://www.ubuntuforums.org/showthread.php?t=282624&highlight=600e](http://www.ubuntuforums.org/showthread.php?t=282624&highlight=600e)

I was attempting to use the same steps to correct it in 6.10. The steps that I have tried on 6.10 are listed blow. Can anyone help a newbie out?

I have run a Linux Server environment for a number of years and thought I would try the desktop side of the house. 

** Steps for 6.06 that work consistently **


Add these lines to /etc/modules:
sound
ad1848
uart401
snd-cs4236

Blacklist the incorrect sound card in /etc/modprobe.d/blacklist. Add these lines to the bottom of the file as written below - with the xx's:
# IBM 600e Sound
blacklist snd-cs46xx
blacklist cs46xx

Add the following lines to the bottom of /etc/modprobe.d/alsa-base:
# IBM 600e Sound
alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

 NOTE: When copying and pasting the above, make sure that the line starting with 'options...' is one line ending with '...dma2=0'.

When using the kernel that came with Ubuntu 6.06 (dapper), I needed to boot the kernel without PNP? support. This is done by adding "pnpbios=off" to the kernel command line; the proper way to do this is to edit /boot/grub/menu.lst, and add pnpbios=off to the line that starts with

# kopt=root=...

and then running grub-update to get those options added to all the kernels that are installed. To run grub-update run the following commands from a terminal.

sudo -i
cd /sbin
./update-grub

You should also go into the BIOS menu (hold down F1 on power-on), and disable "fast boot". Fast boot means that you are using a PNP Operating System. This will prevent the BIOS from configuring the hardware.

Reboot and do not forget that there are 2 places that you must turn up the sound for it to work.

1. Hold down the Fn key and press PgUp repeatedly. You should hear beeps getting progressively louder.

2. On the speaker Icon in the panel.

---

### Post by mseney on 2006-11-25
I also followed your instructions on my 600E (2645-RP1) and get the following: 

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

Module                  Size  Used by
nls_cp437               6912  1 
isofs                  38076  1 
udf                    89348  0 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
nvram                  10376  1 
uinput                 10368  1 
apm                    23280  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
af_packet              24584  2 
snd_cs4236_lib         17920  0 
uart401                12996  0 
ad1848                 32764  0 
sound                  82920  2 uart401,ad1848
lp                     12964  0 
pcnet_cs               39472  1 
8390                   11904  1 pcnet_cs
axnet_cs               20480  1 
tsdev                   9152  0 
snd_opl3_lib           12288  0 
snd_hwdep              10756  1 snd_opl3_lib
snd_cs4231_lib         27520  1 snd_cs4236_lib
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
irtty_sir              10112  0 
sir_dev                18308  1 irtty_sir
snd_pcm                84612  3
snd_cs4236_lib,snd_cs4231_lib,snd_pcm_oss
snd_timer              25348  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd_page_alloc         11400  2 snd_cs4231_lib,snd_pcm
snd_mpu401_uart        10240  0 
snd_rawmidi            27264  1 snd_mpu401_uart
snd_seq_device          9868  2 snd_opl3_lib,snd_rawmidi
irda                  214332  2 irtty_sir,sir_dev
analog                 12960  0 
crc_ccitt               3200  1 irda
psmouse                41352  0 
serio_raw               8452  0 
snd                    58372  11
snd_cs4236_lib,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
ns558                   6016  0 
soundcore              11232  2 sound,snd
evdev                  11392  2 
pcmcia                 40380  2 pcnet_cs,axnet_cs
gameport               17160  3 analog,ns558
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
pcspkr                  4352  0 
floppy                 63044  0 
intel_agp              26012  1 
agpgart                34888  1 intel_agp
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
i2c_piix4              10000  0 
i2c_core               23424  1 i2c_piix4
yenta_socket           28812  6 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  5
pcnet_cs,axnet_cs,pcmcia,yenta_socket,rsrc_nonstatic
ext3                  142728  1 
jbd                    62228  1 ext3
uhci_hcd               24968  0 
usbcore               134912  2 uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  1 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 5764  0 
processor              31560  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

--------------------------------------------------
NOTE: Back in the day when I used Slackware I was able to get the sound working on this thing, been too long to remember what I did. Any help would be appreciated!

EDIT:

I went and used the PS2.EXE CDROM and changed the DMA to 1 0 to match your directions. I made sure to initialize and then disable Quickboot.

Here is my dmesg output (I'm sure it makes sense to someone):

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000009fd0000 (usable)
[17179569.184000]  BIOS-e820: 0000000009fd0000 - 0000000009fdf000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000009fdf000 - 0000000009fe0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000009fe0000 - 000000000a000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 159MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 40912
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 36816 pages, LIFO batch:7
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 IBM                                   ) @ 0x000fd6e0
[17179569.184000] ACPI: RSDT (v001 IBM    TP600R   0x00000001  0x00000000) @ 0x09fd0000
[17179569.184000] ACPI: FADT (v001 IBM    TP600R   0x00000001  0x00000000) @ 0x09fd0100
[17179569.184000] ACPI: DSDT (v001 IBM    TP600R   0x00000104 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0a000000:f5fe0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0114a000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 364.018 MHz processor.
[  298.137076] Using tsc for high-res timesource
[  298.138887] Console: colour VGA+ 80x25
[  298.139758] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[  298.140471] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[  298.169901] Memory: 152580k/163648k available (1910k kernel code, 10520k reserved, 1070k data, 308k init, 0k highmem)
[  298.169923] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  298.248928] Calibrating delay using timer specific routine.. 729.44 BogoMIPS (lpj=1458883)
[  298.249127] Security Framework v1.0.0 initialized
[  298.249160] SELinux:  Disabled at boot.
[  298.249240] Mount-cache hash table entries: 512
[  298.249836] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[  298.249875] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[  298.249924] CPU: L1 I cache: 16K, L1 D cache: 16K
[  298.249939] CPU: L2 cache: 256K
[  298.249954] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[  298.250049] Checking 'hlt' instruction... OK.
[  298.265046] SMP alternatives: switching to UP code
[  298.265504] Freeing SMP alternatives: 16k freed
[  298.266116] checking if image is initramfs... it is
[  300.809500] Freeing initrd memory: 5254k freed
[  300.809532] CPU0: Intel Mobile Pentium II stepping 0a
[  300.809561] SMP motherboard not detected.
[  300.809574] Local APIC not detected. Using dummy APIC emulation.
[  300.809887] Brought up 1 CPUs
[  300.809984] migration_cost=0
[  300.811445] NET: Registered protocol family 16
[  300.811604] EISA bus registered
[  300.814043] PCI: PCI BIOS revision 2.10 entry at 0xfd880, last bus=7
[  300.814071] PCI: Using configuration type 1
[  300.814083] Setting up standard PCI resources
[  300.815712] ACPI: Interpreter disabled.
[  300.815734] Linux Plug and Play Support v0.97 (c) Adam Belay
[  300.815772] pnp: PnP ACPI: disabled
[  300.815788] PnPBIOS: Scanning system for PnP BIOS support...
[  300.815953] PnPBIOS: Found PnP BIOS installation structure at 0xc00fe700
[  300.815972] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xe724, dseg 0xf0000
[  300.911201] PnPBIOS: 23 nodes reported by PnP BIOS; 23 recorded by driver
[  300.911446] PCI: Probing PCI hardware
[  300.911465] PCI: Probing PCI hardware (bus 00)
[  300.912253] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[  300.912470] PCI quirk: region ef00-ef3f claimed by PIIX4 ACPI
[  300.912488] PCI quirk: region efa0-efaf claimed by PIIX4 SMB
[  300.912507] PIIX4 devres B PIO at 02f8-02ff
[  300.912522] PIIX4 devres C PIO at 15e8-15ef
[  300.912536] PIIX4 devres E PIO at 0538-053f
[  300.912553] PIIX4 devres G PIO at 0130-013f
[  300.912570] PIIX4 devres I PIO at 002e-002f
[  300.912929] Boot video device is 0000:01:00.0
[  300.915762] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[  300.926443] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[  300.926463] pnp: 00:0a: ioport range 0x15e0-0x15ef has been reserved
[  300.926481] pnp: 00:0a: ioport range 0xef00-0xefaf could not be reserved
[  300.927769] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[  300.927785] PCI: Bridge: 0000:00:01.0
[  300.927799]   IO window: d000-dfff
[  300.927818]   MEM window: 70000000-dfffffff
[  300.927835]   PREFETCH window: e0000000-f7ffffff
[  300.927853] PCI: Bus 2, cardbus bridge: 0000:00:02.0
[  300.927866]   IO window: 00001000-000010ff
[  300.927882]   IO window: 00001400-000014ff
[  300.927898]   PREFETCH window: 10000000-11ffffff
[  300.927915]   MEM window: 12000000-13ffffff
[  300.927931] PCI: Bus 6, cardbus bridge: 0000:00:02.1
[  300.927943]   IO window: 00001800-000018ff
[  300.927958]   IO window: 00001c00-00001cff
[  300.927975]   PREFETCH window: 14000000-15ffffff
[  300.927991]   MEM window: 16000000-17ffffff
[  300.928053] PCI: Found IRQ 11 for device 0000:00:02.0
[  300.928078] PCI: Sharing IRQ 11 with 0000:00:06.0
[  300.928103] PCI: Sharing IRQ 11 with 0000:01:00.0
[  300.928142] PCI: Found IRQ 11 for device 0000:00:02.1
[  300.928299] NET: Registered protocol family 2
[  300.964968] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[  300.965443] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[  300.965810] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[  300.966003] TCP: Hash tables configured (established 8192 bind 4096)
[  300.966018] TCP reno registered
[  300.969552] audit: initializing netlink socket (disabled)
[  300.969608] audit(1164471447.984:1): initialized
[  300.970293] VFS: Disk quotas dquot_6.5.1
[  300.970394] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  300.970666] Initializing Cryptographic API
[  300.970689] io scheduler noop registered
[  300.970720] io scheduler anticipatory registered
[  300.970752] io scheduler deadline registered
[  300.970821] io scheduler cfq registered (default)
[  300.970846] Limiting direct PCI/PCI transfers.
[  300.971868] isapnp: Scanning for PnP cards...
[  301.328073] isapnp: No Plug & Play device found
[  301.480421] Real Time Clock Driver v1.12ac
[  301.480784] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  301.481118] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[  301.484324] pnp: Unable to assign resources to device 00:0d.
[  301.484407] serial: probe of 00:0d failed with error -16
[  301.485784] mice: PS/2 mouse device common for all mice
[  301.488946] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  301.489608] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  301.489629] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  301.490482] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[  301.503792] serio: i8042 AUX port at 0x60,0x64 irq 12
[  301.505197] serio: i8042 KBD port at 0x60,0x64 irq 1
[  301.508032] EISA: Probing bus 0 at eisa.0
[  301.508064] Cannot allocate resource for EISA slot 1
[  301.508119] Cannot allocate resource for EISA slot 8
[  301.508130] EISA: Detected 0 cards.
[  301.508596] TCP bic registered
[  301.508633] NET: Registered protocol family 1
[  301.508665] NET: Registered protocol family 8
[  301.508677] NET: Registered protocol family 20
[  301.508787] Using IPI No-Shortcut mode
[  301.510672] Freeing unused kernel memory: 308k freed
[  301.530183] input: AT Translated Set 2 keyboard as /class/input/input0
[  303.030548] Capability LSM initialized
[  305.678047] PIIX4: IDE controller at PCI slot 0000:00:07.1
[  305.678102] PIIX4: chipset revision 1
[  305.678114] PIIX4: not 100% native mode: will probe irqs later
[  305.678144]     ide0: BM-DMA at 0xfcf0-0xfcf7, BIOS settings: hda:DMA, hdb:pio
[  305.678190]     ide1: BM-DMA at 0xfcf8-0xfcff, BIOS settings: hdc:DMA, hdd:pio
[  305.678222] Probing IDE interface ide0...
[  305.964178] hda: IBM-DBCA-206480, ATA DISK drive
[  306.636406] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[  306.637367] Probing IDE interface ide1...
[  307.372000] hdc: TOSHIBA CD-ROM XM-1902B, ATAPI CD/DVD-ROM drive
[  307.729299] ide1 at 0x170-0x177,0x376 on irq 15
[  307.763769] hda: max request size: 128KiB
[  307.831219] hda: 12594960 sectors (6448 MB) w/420KiB Cache, CHS=13328/15/63, UDMA(33)
[  307.831256] hda: cache flushes not supported
[  307.831422]  hda: hda1 hda2 < hda5 >
[  308.016274] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, DMA
[  308.016314] Uniform CD-ROM driver Revision: 3.20
[  308.610087] usbcore: registered new driver usbfs
[  308.611818] usbcore: registered new driver hub
[  308.620419] USB Universal Host Controller Interface driver v3.0
[  308.620614] PCI: Found IRQ 11 for device 0000:00:07.2
[  308.620685] uhci_hcd 0000:00:07.2: UHCI Host Controller
[  308.621151] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[  308.621222] uhci_hcd 0000:00:07.2: irq 11, io base 0x00008400
[  308.621626] usb usb1: configuration #1 chosen from 1 choice
[  308.621782] hub 1-0:1.0: USB hub found
[  308.621832] hub 1-0:1.0: 2 ports detected
[  308.891789] Attempting manual resume
[  308.980239] kjournald starting.  Commit interval 5 seconds
[  308.980296] EXT3-fs: mounted filesystem with ordered data mode.
[  335.403497] PCI: Found IRQ 11 for device 0000:00:02.0
[  335.403531] PCI: Sharing IRQ 11 with 0000:00:06.0
[  335.403559] PCI: Sharing IRQ 11 with 0000:01:00.0
[  335.403591] Yenta: CardBus bridge found at 0000:00:02.0 [1014:00eb]
[  335.403625] Yenta: Enabling burst memory read transactions
[  335.403641] Yenta: Using CSCINT to route CSC interrupts to PCI
[  335.403653] Yenta: Routing CardBus interrupts to PCI
[  335.403671] Yenta TI: socket 0000:00:02.0, mfunc 0xfba97543, devctl 0x62
[  335.633393] Yenta: ISA IRQ mask 0x0698, PCI irq 11
[  335.633411] Socket status: 30000010
[  335.634944] PCI: Found IRQ 11 for device 0000:00:02.1
[  335.635013] Yenta: CardBus bridge found at 0000:00:02.1 [1014:00eb]
[  335.635051] Yenta: Using CSCINT to route CSC interrupts to PCI
[  335.635064] Yenta: Routing CardBus interrupts to PCI
[  335.635083] Yenta TI: socket 0000:00:02.1, mfunc 0xfba97543, devctl 0x62
[  335.645911] input: PC Speaker as /class/input/input1
[  335.686120] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  336.372408] pccard: PCMCIA card inserted into slot 0
[  336.621388] Yenta: ISA IRQ mask 0x0698, PCI irq 11
[  336.621409] Socket status: 30000010
[  337.311891] Linux agpgart interface v0.101 (c) Dave Jones
[  337.412272] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[  337.412299] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
[  337.412324] piix4_smbus: probe of 0000:00:07.3 failed with error -1
[  337.412676] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  337.475091] agpgart: Detected an Intel 440BX Chipset.
[  337.484808] agpgart: AGP aperture is 64M @ 0x40000000
[  337.852819] Floppy drive(s): fd0 is 1.44M
[  337.870073] FDC 0 is a National Semiconductor PC87306
[  338.384156] pccard: PCMCIA card inserted into slot 1
[  339.531719] parport: PnPBIOS parport detected.
[  339.531789] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[  341.406462] irda_init()
[  341.406530] NET: Registered protocol family 23
[  341.515127] nsc_ircc_pnp_probe() : From PnP, found firbase 0x3F8 ; irq 4 ; dma 3.
[  341.515184] nsc-ircc, chip->init
[  341.515197] nsc-ircc, Found chip at base=0x02e
[  341.515238] nsc-ircc, driver loaded (Dag Brattli)
[  341.515267] nsc_ircc_open(), can't get iobase of 0x3f8
[  341.515302] nsc-ircc, Found chip at base=0x02e
[  341.515343] nsc-ircc, driver loaded (Dag Brattli)
[  341.515359] nsc_ircc_open(), can't get iobase of 0x3f8
[  341.529272] pnp: Device 00:13 disabled.
[  341.679286] gameport: NS558 PnP Gameport is pnp00:10/gameport0, io 0x200, speed 677kHz
[  341.836489] cs: IO port probe 0x100-0x3af: excluding 0x130-0x137 0x220-0x22f 0x388-0x38f
[  341.837780] cs: IO port probe 0x3e0-0x4ff: clean.
[  341.838374] cs: IO port probe 0x820-0x8ff: clean.
[  341.839382] cs: IO port probe 0xc00-0xcf7: clean.
[  341.840368] cs: IO port probe 0xa00-0xaff: clean.
[  341.840947] cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[  341.841039] cs: memory probe 0x60000000-0x60ffffff: clean.
[  341.849384] pcmcia: registering new device pcmcia0.0
[  341.998189] logips2pp: Detected unknown logitech mouse model 1
[  342.294856] input: PS/2 Logitech Mouse as /class/input/input2
[  342.529311] CS4232 WSS PnP manual resources are invalid, using auto config
[  342.529335] CS4232 WSS PnP configure failed for WSS (out of resources?)
[  342.529349] PnP BIOS detection failed for CS4232
[  342.548948] pnp: Device 00:0e disabled.
[  342.549125] cs4232-pnpbios: probe of 00:0e failed with error -16
[  342.549246] CS4232 soundcard not found or device busy
[  342.762291] pnp: Device 00:0e activated.
[  342.762432] CS4232 WSS PnP manual resources are invalid, using auto config
[  342.762451] CS4232 WSS PnP configure failed for WSS (out of resources?)
[  342.762464] PnP BIOS detection failed for CS4232
[  342.781993] pnp: Device 00:0e disabled.
[  342.782009] cs4232-pnpbios: probe of 00:0e failed with error -16
[  342.782131] CS4232 soundcard not found or device busy
[  342.853383] cs: IO port probe 0x100-0x3af: excluding 0x130-0x137
[  342.854652] cs: IO port probe 0x3e0-0x4ff: clean.
[  342.855239] cs: IO port probe 0x820-0x8ff: clean.
[  342.855807] cs: IO port probe 0xc00-0xcf7: clean.
[  342.856741] cs: IO port probe 0xa00-0xaff: clean.
[  342.857319] cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[  342.857411] cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x600fffff
[  342.864597] pcmcia: registering new device pcmcia1.0
[  344.177298] ts: Compaq touchscreen protocol output
[  344.605787] eth0: NE2000 Compatible: io 0x300, irq 3, hw_addr 00:40:F4:29:57:B9
[  344.900212] eth1: Asix AX88190: io 0x320, irq 4, hw_addr 00:04:5A:92:9E:57
[  345.713602] lp0: using parport0 (interrupt-driven).
[  345.927025] ad1848/cs4248 codec driver Copyright (C) by Hannu Savolainen 1993-1996
[  345.927082] ad1848: No ISAPnP cards found, trying standard ones...
[  346.212195] CS4236+ soundcard not found or device busy
[  346.375291] Adding 297160k swap on /dev/disk/by-uuid/ba52b709-0069-405a-b489-7e849c01016e.  Priority:-1 extents:1 across:297160k
[  346.508323] NET: Registered protocol family 17
[  346.575264] EXT3 FS on hda1, internal journal
[  347.387079] eth0: interrupt(s) dropped!
[  348.522906] eth0: interrupt(s) dropped!
[  365.931174] IBM machine detected. Enabling interrupts during APM calls.
[  365.931207] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  377.394126] ttyS0: LSR safety check engaged!
[  383.928706] Non-volatile memory driver v1.2
[  384.074793] input: /usr/sbin/thinkpad-keys as /class/input/input3
[  385.094257] Bluetooth: Core ver 2.8
[  385.094289] NET: Registered protocol family 31
[  385.094301] Bluetooth: HCI device and connection manager initialized
[  385.094361] Bluetooth: HCI socket layer initialized
[  385.230260] Bluetooth: L2CAP ver 2.8
[  385.230287] Bluetooth: L2CAP socket layer initialized
[  385.256924] Bluetooth: RFCOMM socket layer initialized
[  385.256994] Bluetooth: RFCOMM TTY layer initialized
[  385.257007] Bluetooth: RFCOMM ver 1.7

---

### Post by mseney on 2006-11-26
Well I figured out that I somehow didn't edit the Grub Menu correctly and so "pnpbios=off" wasn't in there. I manually did it when booting by pressing "e" and then selecting the Kernel entry, hitting "e" again and adding it on the end. Press <enter> and press "b" to boot. Only problem with this is it doesn't keep the setting. I just manually edited the /boot/grub/menu.lst and added "pnpbios=off" to then end of this line:

Kernel     /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash ## right here ##

All in all, your directions did work excellent and I can play music and have sound in gnometris *yay* Thanks!!!!

---

### Post by mayankjohri on 2006-12-07
You can add the entry by updating the /boot/grub/menu.lst file.

---

### Post by vroomfondel on 2007-01-02
I tried the same release on my 600E but the video speed was so bad it was unusable.
Was prepared for problems with wifi card and not really bothered about sound, but if basic desktop is so slow then its not worth going further.
edit: found suggestion to set depth to 16 bit and that improved video no end.
Now discovered pccard slot isn't detected ...

---

### Post by bchurchwell on 2007-01-20
I can confirm that the steps in post #1 worked on my 600E.

---

### Post by MichaelGu on 2007-02-09
I fixed it occasionally in IBM 600E model 2645-4AH with Ubuntu 6.10 edgy (Alternate)

Here with detail,
1.Disable Quick Boot in BIOS
2.Disable PCIBUSPowermanagement with PS2
3.Modify menu.lst
Kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash _pnpbios=off_
4.Blacklist the incorrect sound card in /etc/modprobe.d/blacklist. Add these lines to the bottom of the file as written below - with the xx's:
# IBM 600e Sound
blacklist snd-cs46xx
blacklist cs46xx
5.Add these lines to /etc/modules:
snd-cs4236 isapnp=0 cport=0x538 port=0x530 irq=5 dma1=1 dma2=0
snd-cs4236 isapnp=0 cport=0x538 port=0x530 irq=5 dma1=1 dma2=0
snd-cs4236 isapnp=0 cport=0x538 port=0x530 irq=5 dma1=1 dma2=0
P.S. replicate 3 times

As you read message of "DMESG" it seems loading snd-cs4236 in error. Meanwhile sound works.
No need to modify alsa-base.
I have no idea on how it works.

I found solution in way of modprobe sound-cs4236 ******** 2 times in terminal.
But 2-time loading in module does not work. 
Therefore I add 3-time loading in module and it comes work.:guitar:

---

