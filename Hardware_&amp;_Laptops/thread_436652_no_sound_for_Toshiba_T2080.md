---
title: "no sound for Toshiba T2080"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by adameye on 2007-05-08
I followed [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
however I can not find driver for my laptop
I tried [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Toshiba&card=Satellite+Pro+4200.&chip=YMF744&module=ymfpci](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Toshiba&card=Satellite+Pro+4200.&chip=YMF744&module=ymfpci)
however, when I use command [COLOR="Red"]./configure --with-cards=ymfpci --with-sequencer=yes;make;make install[/COLOR]

./configure --with-cards=ymfpci --with-sequencer=yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.13
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.20-15-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.20-15-generic
checking for GCC version... Kernel compiler: gcc 4.1.2 (Ubuntu 4.1.2-0ubuntu4) Used compiler: gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
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
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.20-15-generic/kernel/sound
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
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for V4L1 layer... yes
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver version... 1.0.13
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... no
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... ymfpci
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...

---

### Post by adameye on 2007-05-08
**[COLOR="Red"] lspci[/COLOR]**
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


[COLOR="Red"]**lsmod**[/COLOR]
Module Size Used by
binfmt_misc 12680 1
rfcomm 40856 0
l2cap 25728 5 rfcomm
bluetooth 55908 4 rfcomm,l2cap
ppdev 10116 0
acpi_cpufreq 10056 1
cpufreq_powersave 2688 0
cpufreq_userspace 5408 0
cpufreq_ondemand 9228 1
cpufreq_stats 7360 0
freq_table 5792 3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative 8200 0
tc1100_wmi 8068 0
sony_acpi 6284 0
dev_acpi 12292 0
pcc_acpi 13184 0
sbs 15652 0
ac 6020 0
container 5248 0
asus_acpi 17308 0
backlight 7040 1 asus_acpi
button 8720 0
video 16388 0
i2c_ec 5888 1 sbs
dock 10268 0
battery 10756 0
ipv6 268704 10
nls_utf8 3072 2
ntfs 107764 2
gameport 16520 0
ac97_bus 3456 0
parport_pc 36388 0
lp 12452 0
parport 36936 3 ppdev,parport_pc,lp
fuse 46612 0
joydev 10816 0
wlan_scan_sta 14976 1
ath_rate_sample 14080 1
pcmcia 39212 0
ath_pci 97312 0
wlan 204484 4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal 192592 3 ath_rate_sample,ath_pci
i2c_piix4 9740 0
ati_agp 10124 0
agpgart 35400 1 ati_agp
yenta_socket 27532 1
rsrc_nonstatic 14080 1 yenta_socket
pcmcia_core 40852 3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core 22784 2 i2c_ec,i2c_piix4
serio_raw 7940 0
shpchp 34324 0
pci_hotplug 32576 1 shpchp
psmouse 38920 0
soundcore 8672 0
pcspkr 4224 0
af_packet 23816 6
tsdev 8768 0
evdev 11008 4
ext3 133128 1
jbd 59816 1 ext3
mbcache 9604 1 ext3
sg 36252 0
sd_mod 23428 5
ide_cd 32672 0
cdrom 37664 1 ide_cd
8139too 27648 0
generic 5124 0 [permanent]
sata_sil 12808 4
atiixp 7440 0 [permanent]
ata_generic 9092 0
libata 125720 2 sata_sil,ata_generic
ehci_hcd 34188 0
scsi_mod 142348 3 sg,sd_mod,libata
8139cp 25088 0
mii 6528 2 8139too,8139cp
ohci_hcd 22532 0
usbcore 134280 3 ehci_hcd,ohci_hcd
thermal 14856 0
processor 31048 2 acpi_cpufreq,thermal
fan 5636 0
fbcon 42656 0
tileblit 3584 1 fbcon
font 9216 1 fbcon
bitblit 6912 1 fbcon
softcursor 3200 1 bitblit
vesafb 9220 0
capability 5896 0
commoncap 8192 1 capability


**[COLOR="Red"]dmesg[/COLOR]**
.....
[ 13.947287] CPU1: Intel Genuine Intel(R) CPU T2080 @ 1.73GHz stepping 0c
[ 13.947314] Total of 2 processors activated (6937.98 BogoMIPS).
[ 13.947496] ENABLING IO-APIC IRQs
[ 13.947711] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[ 14.094636] checking TSC synchronization across 2 CPUs: passed.
[ 0.003999] Brought up 2 CPUs
[ 0.165031] migration_cost=132
[ 0.165348] Booting paravirtualized kernel on bare hardware
[ 0.165456] Time: 10:04:46 Date: 04/08/107
[ 0.165492] NET: Registered protocol family 16
[ 0.165592] EISA bus registered
[ 0.165600] ACPI: bus type pci registered
[ 0.183442] PCI: PCI BIOS revision 2.10 entry at 0xfd5b4, last bus=14
[ 0.183445] PCI: Using configuration type 1
[ 0.183447] Setting up standard PCI resources
[ 0.190910] ACPI Error (evregion-0317): No handler for Region [ERAM] (da0f0484) [EmbeddedControl] [20060707]
[ 0.190917] ACPI Error (exfldio-0290): Region EmbeddedControl(3) has no handler [20060707]
[ 0.190922] ACPI Exception (dswexec-045: AE_NOT_EXIST, While resolving operands for [OpcodeName unavailable] [20060707]
[ 0.190928] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.HTEV] (Node da0e8e8c), AE_NOT_EXIST
[ 0.190963] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node da0f1f2c), AE_NOT_EXIST
[ 0.192687] APIC error on CPU1: 00(40)
[ 0.201291] ACPI: Interpreter enabled
[ 0.201296] ACPI: Using IOAPIC for interrupt routing
[ 0.203170] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 0.203180] PCI: Probing PCI hardware (bus 00)
[ 0.206014] Boot video device is 0000:01:05.0
[ 0.206631] PCI: Transparent bridge - 0000:00:14.4
[ 0.206812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.212051] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[ 0.220061] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[ 0.220647] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[ 0.221220] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[ 0.221797] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[ 0.222378] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[ 0.222952] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[ 0.223529] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[ 0.224171] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[ 0.224755] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[ 0.267912] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[ 0.268983] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[ 0.270389] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 0.270407] pnp: PnP ACPI init
[ 0.295973] pnp: PnP ACPI: found 10 devices
[ 0.295981] PnPBIOS: Disabled by ACPI PNP
[ 0.296070] PCI: Using ACPI for IRQ routing
[ 0.296076] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[ 0.332842] NET: Registered protocol family 8
[ 0.332847] NET: Registered protocol family 20
[ 0.333306] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[ 0.333313] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[ 0.333319] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[ 0.333324] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[ 0.333905] PCI: Bridge: 0000:00:01.0
[ 0.333910] IO window: 9000-9fff
[ 0.333918] MEM window: d0000000-d00fffff
[ 0.333925] PREFETCH window: d8000000-dfffffff
[ 0.333932] PCI: Bridge: 0000:00:06.0
[ 0.333935] IO window: disabled.
[ 0.333943] MEM window: d0100000-d01fffff
[ 0.333948] PREFETCH window: disabled.
[ 0.333971] PCI: Bus 10, cardbus bridge: 0000:09:04.0
[ 0.333975] IO window: 0000a400-0000a4ff
[ 0.333985] IO window: 0000a800-0000a8ff
[ 0.333994] PREFETCH window: 24000000-27ffffff
[ 0.334004] MEM window: 28000000-2bffffff
[ 0.334013] PCI: Bridge: 0000:00:14.4
[ 0.334019] IO window: a000-afff
[ 0.334030] MEM window: f0200000-f02fffff
[ 0.334039] PREFETCH window: f0300000-f03fffff
[ 0.334076] PCI: Setting latency timer of device 0000:00:06.0 to 64
[ 0.334117] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 17 (level, low) -> IRQ 16
[ 0.334183] NET: Registered protocol family 2
[ 0.367692] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[ 0.367852] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[ 0.368046] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[ 0.368146] TCP: Hash tables configured (established 16384 bind 8192)
[ 0.368151] TCP reno registered
[ 0.379798] checking if image is initramfs... it is
[ 1.803503] Freeing initrd memory: 7006k freed
[ 1.804802] audit: initializing netlink socket (disabled)
[ 1.804835] audit(1178618686.592:1): initialized
[ 1.805175] VFS: Disk quotas dquot_6.5.1
[ 1.805219] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1.805315] io scheduler noop registered
[ 1.805321] io scheduler anticipatory registered
[ 1.805326] io scheduler deadline registered
[ 1.805350] io scheduler cfq registered (default)
[ 1.805709] PCI: Setting latency timer of device 0000:00:06.0 to 64
[ 1.805766] assign_interrupt_mode Found MSI capability
[ 1.805773] Allocate Port Service[0000:00:06.0cie00]
[ 1.805849] Allocate Port Service[0000:00:06.0cie02]
[ 1.806166] isapnp: Scanning for PnP cards...
[ 2.163211] isapnp: No Plug & Play device found
[ 2.213975] Real Time Clock Driver v1.12ac
[ 2.214101] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 2.215414] mice: PS/2 mouse device common for all mice
[ 2.216585] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 2.216896] input: Macintosh mouse button emulation as /class/input/input0
[ 2.216971] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 2.216978] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 2.217422] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[ 2.217874] i8042.c: Detected active multiplexing controller, rev 1.1.
[ 2.217970] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 2.217979] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[ 2.217985] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[ 2.217991] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[ 2.217996] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[ 2.218181] EISA: Probing bus 0 at eisa.0
[ 2.218200] Cannot allocate resource for EISA slot 1
[ 2.218243] Cannot allocate resource for EISA slot 8
[ 2.218247] EISA: Detected 0 cards.
[ 2.237481] input: AT Translated Set 2 keyboard as /class/input/input1
[ 2.248401] TCP cubic registered
[ 2.248417] NET: Registered protocol family 1
[ 2.248461] Starting balanced_irq
[ 2.248474] Using IPI No-Shortcut mode
[ 2.248595] ACPI: (supports S0 S3 S4 S5)
[ 2.248692] Magic number: 7:166:72
[ 2.249270] Time: tsc clocksource has been installed.
[ 2.249426] Freeing unused kernel memory: 328k freed
[ 3.643505] Capability LSM initialized
[ 3.719200] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[ 3.720682] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[ 3.721318] ACPI: CPU0 (power states: C1[C1] C3[C3])
[ 3.721328] ACPI: Processor [CPU0] (supports 8 throttling states)
[ 3.722593] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[ 3.723186] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[ 3.723868] ACPI: CPU1 (power states: C1[C1] C3[C3])
[ 3.723878] ACPI: Processor [CPU1] (supports 8 throttling states)
[ 3.723893] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 3.723908] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 3.723924] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 3.723938] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 3.723951] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 3.723965] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 4.387140] usbcore: registered new interface driver usbfs
[ 4.387189] usbcore: registered new interface driver hub
[ 4.387236] usbcore: registered new device driver usb
[ 4.388912] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[ 4.388986] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[ 4.389014] ohci_hcd 0000:00:13.0: OHCI Host Controller
[ 4.389253] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[ 4.389291] ohci_hcd 0000:00:13.0: irq 17, io mem 0xd0504000
[ 4.427171] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[ 4.438011] SCSI subsystem initialized
[ 4.451783] libata version 2.20 loaded.
[ 4.454875] usb usb1: configuration #1 chosen from 1 choice
[ 4.454937] hub 1-0:1.0: USB hub found
[ 4.454960] hub 1-0:1.0: 4 ports detected
[ 4.559471] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[ 4.559503] ohci_hcd 0000:00:13.1: OHCI Host Controller
[ 4.559739] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[ 4.559768] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd0505000
[ 4.614634] usb usb2: configuration #1 chosen from 1 choice
[ 4.614691] hub 2-0:1.0: USB hub found
[ 4.614713] hub 2-0:1.0: 4 ports detected
[ 4.718537] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[ 4.718568] ehci_hcd 0000:00:13.2: EHCI Host Controller
[ 4.718619] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[ 4.718692] ehci_hcd 0000:00:13.2: irq 17, io mem 0xd0506000
[ 4.718709] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 4.718858] usb usb3: configuration #1 chosen from 1 choice
[ 4.718912] hub 3-0:1.0: USB hub found
[ 4.718925] hub 3-0:1.0: 8 ports detected
[ 4.825443] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[ 4.825478] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[ 4.825499] ATIIXP: chipset revision 128
[ 4.825503] ATIIXP: not 100% native mode: will probe irqs later
[ 4.825522] ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdcMA, hddio
[ 4.825541] Probing IDE interface ide1...
[ 5.561719] hdc: HL-DT-ST DVDRAM GMA-4082N, ATAPI CD/DVD-ROM drive
[ 6.384000] Time: acpi_pm clocksource has been installed.
[ 6.508000] ide1 at 0x170-0x177,0x376 on irq 15
[ 6.512000] sata_sil 0000:00:12.0: version 2.2
[ 6.512000] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[ 6.512000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 19
[ 6.512000] ata1: SATA max UDMA/100 cmd 0xdc8ae080 ctl 0xdc8ae08a bmdma 0xdc8ae000 irq 19
[ 6.512000] ata2: SATA max UDMA/100 cmd 0xdc8ae0c0 ctl 0xdc8ae0ca bmdma 0xdc8ae008 irq 19
[ 6.512000] scsi0 : sata_sil
[ 6.980000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 6.988000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[ 6.988000] ata1.00: ATA-8: FUJITSU MHW2080BH, 00000012, max UDMA/100
[ 6.988000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[ 6.996000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[ 6.996000] ata1.00: configured for UDMA/100
[ 6.996000] scsi1 : sata_sil
[ 7.308000] ata2: SATA link down (SStatus 0 SControl 300)
[ 7.308000] scsi 0:0:0:0: Direct-Access ATA FUJITSU MHW2080B 0000 PQ: 0 ANSI: 5
[ 7.308000] 8139cp 0000:09:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[ 7.308000] 8139cp 0000:09:06.0: Try the "8139too" driver instead.
[ 7.316000] 8139too Fast Ethernet driver 0.9.28
[ 7.320000] ACPI: PCI Interrupt 0000:09:06.0[A] -> GSI 22 (level, low) -> IRQ 19
[ 7.320000] eth0: RealTek RTL8139 at 0xdc888000, 00:16:d4:97:63:83, IRQ 19
[ 7.320000] eth0: Identified 8139 chip type 'RTL-8100B/8139D'
[ 7.328000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[ 7.328000] Uniform CD-ROM driver Revision: 3.20
[ 7.332000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 7.332000] sda: Write Protect is off
[ 7.332000] sda: Mode Sense: 00 3a 00 00
[ 7.332000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7.332000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 7.332000] sda: Write Protect is off
[ 7.332000] sda: Mode Sense: 00 3a 00 00
[ 7.332000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7.332000] sda: sda1 sda2 sda3 sda4
[ 7.404000] sd 0:0:0:0: Attached scsi disk sda
[ 7.408000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 7.792000] Attempting manual resume
[ 7.792000] swsusp: Resume From Partition 8:4
[ 7.792000] PM: Checking swsusp image.
[ 7.792000] PM: Resume from disk failed.
[ 7.824000] kjournald starting. Commit interval 5 seconds
[ 7.824000] EXT3-fs: mounted filesystem with ordered data mode.
[ 18.156000] eth0: link down
[ 19.440000] NET: Registered protocol family 17
[ 20.192000] input: PC Speaker as /class/input/input2
[ 20.488000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 20.508000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 20.564000] Yenta: CardBus bridge found at 0000:09:04.0 [1179:ff00]
[ 20.564000] Yenta: Using CSCINT to route CSC interrupts to PCI
[ 20.564000] Yenta: Routing CardBus interrupts to PCI
[ 20.564000] Yenta TI: socket 0000:09:04.0, mfunc 0x00111c12, devctl 0x44
[ 20.676000] Linux agpgart interface v0.102 (c) Dave Jones
[ 20.772000] ath_hal: module license 'Proprietary' taints kernel.
[ 20.780000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 20.796000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 16
[ 20.796000] Socket status: 30000006
[ 20.796000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[ 20.796000] cs: IO port probe 0xa000-0xafff: clean.
[ 20.796000] pcmcia: parent PCI bridge Memory window: 0xf0200000 - 0xf02fffff
[ 20.796000] pcmcia: parent PCI bridge Memory window: 0xf0300000 - 0xf03fffff
[ 20.796000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[ 20.880000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[ 20.880000] synaptics: Toshiba Satellite A135 detected, limiting rate to 40pps.
[ 20.908000] wlan: 0.8.4.2 (0.9.3)
[ 20.912000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[ 20.940000] ath_pci: 0.9.4.5 (0.9.3)
[ 20.940000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 20
[ 20.940000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[ 21.480000] ath_rate_sample: 1.2 (0.9.3)
[ 21.480000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[ 21.480000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 21.480000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[ 21.480000] wifi0: mac 10.0 phy 6.1 radio 10.2
[ 21.480000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[ 21.480000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[ 21.480000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[ 21.480000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[ 21.480000] wifi0: Use hw queue 8 for CAB traffic
[ 21.480000] wifi0: Use hw queue 9 for beacons
[ 21.504000] wifi0: Atheros 5424/2424: mem=0xd0100000, irq=20
[ 21.696000] cs: IO port probe 0x100-0x3af: clean.
[ 21.720000] cs: IO port probe 0x3e0-0x4ff: clean.
[ 21.720000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[ 21.720000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[ 21.720000] cs: IO port probe 0xa00-0xaff: clean.
[ 21.872000] fuse init (API version 7.
[ 21.968000] lp: driver loaded but no devices found
[ 22.168000] Adding 489972k swap on /dev/disk/by-uuid/c99ad3ea-74c5-43b3-8f0d-02da58769809. Priority:-1 extents:1 across:489972k
[ 22.328000] EXT3 FS on sda3, internal journal
[ 22.604000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[ 22.680000] NTFS volume version 3.1.
[ 22.728000] NTFS volume version 3.1.
[ 24.592000] NET: Registered protocol family 10
[ 24.592000] lo: Disabled Privacy Extensions
[ 24.592000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 27.880000] ACPI: Battery Slot [BAT1] (battery present)
[ 27.912000] No dock devices found.
[ 27.992000] ACPI: Video Device [VGA] (multi-head: yes rom: no post: no)
[ 28.024000] input: Power Button (FF) as /class/input/input4
[ 28.024000] ACPI: Power Button (FF) [PWRF]
[ 28.024000] input: Lid Switch as /class/input/input5
[ 28.024000] ACPI: Lid Switch [LID]
[ 28.024000] input: Power Button (CM) as /class/input/input6
[ 28.024000] ACPI: Power Button (CM) [PWRB]
[ 28.272000] ibm_acpi: ec object not found
[ 28.340000] ACPI: AC Adapter [ACAD] (on-line)
[ 28.472000] Using specific hotkey driver
[ 28.544000] pcc_acpi: loading...
[ 34.456000] ppdev: user-space parallel port driver
[ 34.740000] ath0: no IPv6 routers present
[ 35.144000] apm: BIOS not found.
[ 35.284000] Bluetooth: Core ver 2.11
[ 35.284000] NET: Registered protocol family 31
[ 35.284000] Bluetooth: HCI device and connection manager initialized
[ 35.284000] Bluetooth: HCI socket layer initialized
[ 35.296000] Bluetooth: L2CAP ver 2.8
[ 35.296000] Bluetooth: L2CAP socket layer initialized
[ 35.536000] Bluetooth: RFCOMM socket layer initialized
[ 35.536000] Bluetooth: RFCOMM TTY layer initialized
[ 35.536000] Bluetooth: RFCOMM ver 1.8
Edit/Delete Message

---

