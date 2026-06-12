---
title: "USB issues from Dapper to Hardy upgrade"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by petebarchetta on 2009-03-19
As you may be aware i have installed Dapper LTS on the tecra 550cdt, in dapper form the USB ports hotplugged and after a edit of the menu.lst in grub directory adding noapic and irqpoll to the kernel line, it allowed it to work. this is the only file that wasnt upgraded throught the Dapper to Hardy upgrade, Doing a bit more research going through the 
Then looking through the /sys/bus/usb/devices area, I have been unplugging the device and watching the ls command showing the  disappearing and re-appearing when pushed in and out. So shows devices are appearing / seen by machine, in that when plugging it in it displays bad volume etc. going into the  /sys/bus/usb/devices area shows

1-0:1.0 1-1  1-1:1.0 usb1

The second group is the usb device and the first is the hub onboard, again plugging and unplugging shows the device coming online, but the error is still displayed, in Dapper it jumped straight in, with no issues

Just a thought if this is kernel dependant, can Hardy run with a  Dapper kernel??? As these problems seem to have happened since the upgrade.

Also the only file that was kept current was the menu.lst, this surely should not have affected this?

Any ideas?

---

### Post by petebarchetta on 2009-03-20
doing a bit of research i have tried a:
xxxxxx@cassiopeia:~$ sudo lsusb
Bus 001 Device 003: ID 05dc:a701 Lexar Media, Inc. 
Bus 001 Device 001: ID 0000:0000  
xxxxxx@cassiopeia:~$ 
then
cassiopeia:~$ lsmod
Module                  Size  Used by
vfat                   13440  0 
fat                    53020  1 vfat
apm                    21228  1 
ppdev                   9220  0 
ipv6                  266112  6 
cpufreq_userspace       4696  0 
cpufreq_stats           5636  0 
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6428  0 
cpufreq_conservative     7332  0 
iptable_filter          3072  0 
ip_tables              22400  1 iptable_filter
fuse                   38412  0 
lp                     11844  0 
af_packet              22920  6 
snd_opl3sa2            17640  3 
snd_opl3_lib           10624  1 snd_opl3sa2
snd_hwdep               9376  1 snd_opl3_lib
snd_cs4231_lib         26752  1 snd_opl3sa2
snd_mpu401_uart         7808  1 snd_opl3sa2
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
airo_cs                 7940  1 
airo                   72352  1 airo_cs
snd_pcm                89864  3 snd_opl3sa2,snd_cs4231_lib,snd_pcm_oss
snd_seq_dummy           3844  0 
snd_seq_oss            33536  0 
snd_seq_midi            9376  0 
snd_rawmidi            25504  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25220  4 snd_opl3_lib,snd_cs4231_lib,snd_pcm,snd_seq
snd_seq_device          8716  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55268  19 snd_opl3sa2,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_mpu401_uart,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
3c589_cs               14216  1 
soundcore              10208  1 snd
snd_page_alloc         11272  2 snd_cs4231_lib,snd_pcm
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
sg                     37920  0 
pcmcia                 40508  2 airo_cs,3c589_cs
serio_raw               7300  0 
rtc                    13492  0 
pcspkr                  2180  0 
psmouse                36100  0 
floppy                 62148  0 
yenta_socket           28428  6 
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
donauboe               17152  0 
irda                  187068  1 donauboe
crc_ccitt               2304  2 donauboe,irda
sd_mod                 19984  0 
ext3                  135944  7 
jbd                    58772  1 ext3
ide_cd                 33028  0 
cdrom                  38560  1 ide_cd
ide_disk               17664  9 
usb_storage            74304  0 
scsi_mod              139496  3 sg,sd_mod,usb_storage
ide_generic             1536  0 
ohci_hcd               21892  0 
usbcore               130820  3 usb_storage,ohci_hcd
processor              23360  0 
capability              5000  0 
commoncap               7296  1 capability
vga16fb                13704  1 
vgastate               10368  1 vga16fb
fbcon                  42784  72 
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

i'm kinda stumped as it shows in lsusb its there, but it bombs out and says it cannot mount, exact error is "mount: wrong fs type, bad option, bad superblock on dev/sda1,  missing codepage or helper program, or other error" yet it shows up in the places drop down menu, but then bombs out with the error above if you try and access it

usb mice work well on port, but no usb HD can be used????
any thoughts

edit:
NOTE. this worked fine before in dapper before ubuntu HArdy upgrade, the upgrade so far has fubarred both the PCMCIA ports and USB (the PCMCIA has now been sorted)

---

### Post by prshah on 2009-03-20
> **petebarchetta said:**
> says it cannot mount, exact error is "mount: wrong fs type, bad option, bad superblock on dev/sda1,  missing codepage or helper program, or other error"

And it will also say look in dmesg for more information; so plug in the usb (hdd?) and then wait for it to settle about 10 seconds, then post back the information from the below terminal (Applications-Acessories-Terminal) command```
dmesg | tail -24
```

---

### Post by petebarchetta on 2009-03-20
hello,

output of dmsg:
dmesg
[17179569.184000] Linux version 2.6.15-53-386 (buildd@palmer) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sun Jan 25 23:29:51 UTC 2009
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000a020000 (usable)
[17179569.184000]  BIOS-e820: 000000000a020000 - 000000000a040000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fef80000 - 00000000ff000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffe0000 - 00000000fffe6e00 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffe6e00 - 00000000fffe7000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 160MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 40992
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 36896 pages, LIFO batch:7
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI not present.
[17179569.184000] ACPI: Unable to locate RSDP
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0a040000:f4f40000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash vga=791
[17179569.184000] No local APIC present or hardware disabled
[17179569.184000] mapped APIC to ffffd000 (01141000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 266.644 MHz processor.
[   87.333966] Using tsc for high-res timesource
[   87.334459] Console: colour dummy device 80x25
[   87.337512] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   87.341361] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   87.389141] Memory: 151980k/163968k available (1979k kernel code, 11456k reserved, 607k data, 288k init, 0k highmem)
[   87.389187] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   87.467264] Calibrating delay using timer specific routine.. 534.31 BogoMIPS (lpj=1068625)
[   87.467613] Security Framework v1.0.0 initialized
[   87.467683] SELinux:  Disabled at boot.
[   87.467803] Mount-cache hash table entries: 512
[   87.469065] CPU: After generic identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   87.469125] CPU: After vendor identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   87.469177] Intel Pentium with F0 0F bug - workaround enabled.
[   87.469208] CPU: After all inits, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   87.469429] mtrr: v2.0 (20020519)
[   87.469444] CPU: Intel Mobile Pentium MMX stepping 01
[   87.469484] Checking 'hlt' instruction... OK.
[   87.484522] checking if image is initramfs... it is
[   94.474476] Freeing initrd memory: 6668k freed
[   94.612474] NET: Registered protocol family 16
[   94.612900] EISA bus registered
[   94.614905] PCI: PCI BIOS revision 2.10 entry at 0xfd752, last bus=21
[   94.614953] PCI: Using configuration type 1
[   94.618239] ACPI: Subsystem revision 20051216
[   94.618303] ACPI: Interpreter disabled.
[   94.618328] Linux Plug and Play Support v0.97 (c) Adam Belay
[   94.618418] pnp: PnP ACPI: disabled
[   94.618441] PnPBIOS: Scanning system for PnP BIOS support...
[   94.618646] PnPBIOS: Found PnP BIOS installation structure at 0xc00f8e30
[   94.618682] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9114, dseg 0x0
[   94.826563] PnPBIOS: 18 nodes reported by PnP BIOS; 18 recorded by driver
[   94.826866] PCI: Probing PCI hardware
[   94.826894] PCI: Probing PCI hardware (bus 00)
[   94.827767] Boot video device is 0000:00:04.0
[   94.832862] PCI: IRQ 0 for device 0000:00:02.0 doesn't match PIRQ mask - try pci=usepirqmask
[   94.832907] PCI: IRQ 0 for device 0000:00:02.1 doesn't match PIRQ mask - try pci=usepirqmask
[   94.844465] PCI: Bus 1, cardbus bridge: 0000:00:02.0
[   94.844495]   IO window: 00001000-000010ff
[   94.844519]   IO window: 00001400-000014ff
[   94.844545]   PREFETCH window: 10000000-11ffffff
[   94.844570]   MEM window: 12000000-13ffffff
[   94.844594] PCI: Bus 5, cardbus bridge: 0000:00:02.1
[   94.844617]   IO window: 00001800-000018ff
[   94.844640]   IO window: 00001c00-00001cff
[   94.844666]   PREFETCH window: 14000000-15ffffff
[   94.844691]   MEM window: 16000000-17ffffff
[   94.844734] PCI: IRQ 0 for device 0000:00:02.0 doesn't match PIRQ mask - try pci=usepirqmask
[   94.844772] PCI: No IRQ known for interrupt pin A of device 0000:00:02.0. Please try using pci=biosirq.
[   94.844814] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   94.844850] PCI: IRQ 0 for device 0000:00:02.1 doesn't match PIRQ mask - try pci=usepirqmask
[   94.844883] PCI: No IRQ known for interrupt pin B of device 0000:00:02.1. Please try using pci=biosirq.
[   94.844921] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   94.851772] audit: initializing netlink socket (disabled)
[   94.851867] audit(1237580680.508:1): initialized
[   94.853032] VFS: Disk quotas dquot_6.5.1
[   94.853281] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   94.853822] Initializing Cryptographic API
[   94.853861] io scheduler noop registered
[   94.853910] io scheduler anticipatory registered
[   94.853950] io scheduler deadline registered
[   94.854034] io scheduler cfq registered
[   94.855965] isapnp: Scanning for PnP cards...
[   95.209751] isapnp: No Plug & Play device found
[   95.513290] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   95.518471] serio: i8042 AUX port at 0x60,0x64 irq 12
[   95.519142] serio: i8042 KBD port at 0x60,0x64 irq 1
[   95.519683] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   95.520579] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   95.556116] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   95.564007] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   95.564618] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   95.564655] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   95.566313] mice: PS/2 mouse device common for all mice
[   95.568368] EISA: Probing bus 0 at eisa.0
[   95.568421] Cannot allocate resource for EISA slot 1
[   95.568528] EISA: Detected 0 cards.
[   95.568865] NET: Registered protocol family 2
[   95.589904] input: AT Translated Set 2 keyboard as /class/input/input0
[   95.610715] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   95.612371] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[   95.613044] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[   95.613706] TCP: Hash tables configured (established 8192 bind 8192)
[   95.613733] TCP reno registered
[   95.614519] TCP bic registered
[   95.614576] NET: Registered protocol family 1
[   95.614633] NET: Registered protocol family 8
[   95.614654] NET: Registered protocol family 20
[   95.614822] Using IPI Shortcut mode
[   95.615106] Freeing unused kernel memory: 288k freed
[   96.239523] vesafb: framebuffer at 0xf8000000, mapped to 0xcb080000, using 3072k, total 4096k
[   96.239572] vesafb: mode is 1024x768x16, linelength=2048, pages=1
[   96.239599] vesafb: protected mode interface info at c000:7259
[   96.239623] vesafb: scrolling: redraw
[   96.239651] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[   96.239686] vesafb: Mode is VGA compatible
[   96.358450] Console: switching to colour frame buffer device 128x48
[   96.358499] fb0: VESA VGA frame buffer device
[   97.695336] Capability LSM initialized
[  104.526749] usbcore: registered new driver usbfs
[  104.530902] usbcore: registered new driver hub
[  104.547987] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[  104.551981] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[  104.555482] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[  104.555551] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xf7fff000
[  105.118974] hub 1-0:1.0: USB hub found
[  105.119160] hub 1-0:1.0: 2 ports detected
[  105.811107] Probing IDE interface ide0...
[  106.224778] hda: IBM-IC25N020ATDA04-0, ATA DISK drive
[  106.896595] Probing IDE interface ide1...
[  107.760734] hdc: DV-28E-B, ATAPI CD/DVD-ROM drive
[  108.432541] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[  108.432800] ide1 at 0x170-0x177,0x376 on irq 15
[  108.518565] hda: max request size: 128KiB
[  108.755074] hda: 39070080 sectors (20003 MB) w/1806KiB Cache, CHS=38760/16/63
[  108.755120] hda: cache flushes not supported
[  108.756537]  hda: hda1 hda2 < hda5 hda6 hda7 hda8 hda9 > hda3 hda4
[  108.925783] hdc: ATAPI 24X DVD-ROM drive, 256kB Cache
[  108.925838] Uniform CD-ROM driver Revision: 3.20
[  110.775762] Attempting manual resume
[  110.924102] EXT3-fs: mounted filesystem with ordered data mode.
[  110.948220] kjournald starting.  Commit interval 5 seconds
[  145.602735] PCI: IRQ 0 for device 0000:00:02.0 doesn't match PIRQ mask - try pci=usepirqmask
[  145.602791] PCI: No IRQ known for interrupt pin A of device 0000:00:02.0. Please try using pci=biosirq.
[  145.602862] Yenta: CardBus bridge found at 0000:00:02.0 [1179:0001]
[  145.602921] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[  145.602939] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[  146.776321] irq 11: nobody cared (try booting with the "irqpoll" option)
[  146.776393]  [<c013eee2>] __report_bad_irq+0x22/0x80
[  146.776449]  [<c013efd8>] note_interrupt+0x68/0xc0
[  146.776488]  [<c013e89c>] __do_IRQ+0xbc/0xe0
[  146.776553]  [<c010596a>] do_IRQ+0x1a/0x30
[  146.776598]  [<c01040aa>] common_interrupt+0x1a/0x20
[  146.776640]  [<c01214f7>] __do_softirq+0x47/0xb0
[  146.776677]  [<c0121595>] do_softirq+0x35/0x40
[  146.776708]  [<c0121645>] irq_exit+0x35/0x40
[  146.776737]  [<c010596f>] do_IRQ+0x1f/0x30
[  146.776766]  [<c01040aa>] common_interrupt+0x1a/0x20
[  146.776808]  [<cb039abe>] yenta_probe_irq+0x8e/0xe0 [yenta_socket]
[  146.776904]  [<cb039c9b>] yenta_get_socket_capabilities+0x4b/0x70 [yenta_socket]
[  146.776966]  [<cb03a044>] yenta_probe+0x1b4/0x2d0 [yenta_socket]
[  146.777026]  [<c01e769c>] __pci_device_probe+0x3c/0x60
[  146.777071]  [<c01e76df>] pci_device_probe+0x1f/0x40
[  146.777107]  [<c0244c3b>] driver_probe_device+0x3b/0xc0
[  146.777147]  [<c0244d30>] __driver_attach+0x0/0x40
[  146.777176]  [<c0244d6b>] __driver_attach+0x3b/0x40
[  146.777208]  [<c0244318>] bus_for_each_dev+0x48/0x80
[  146.777277]  [<c0244d85>] driver_attach+0x15/0x20
[  146.777310]  [<c0244d30>] __driver_attach+0x0/0x40
[  146.777340]  [<c02447b9>] bus_add_driver+0x69/0xc0
[  146.777374]  [<c01e792a>] __pci_register_driver+0x6a/0xa0
[  146.777411]  [<cb01f00f>] yenta_socket_init+0xf/0x12 [yenta_socket]
[  146.777465]  [<c013826f>] sys_init_module+0x9f/0x1d0
[  146.777504]  [<c0103049>] syscall_call+0x7/0xb
[  146.777550] handlers:
[  146.777567] [<cb387720>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  146.777819] Disabling IRQ #11
[  146.779198] Yenta: ISA IRQ mask 0x06b8, PCI irq 0
[  146.779226] Socket status: 30000011
[  146.887183] PCI: IRQ 0 for device 0000:00:02.1 doesn't match PIRQ mask - try pci=usepirqmask
[  146.887233] PCI: No IRQ known for interrupt pin B of device 0000:00:02.1. Please try using pci=biosirq.
[  146.887306] Yenta: CardBus bridge found at 0000:00:02.1 [1179:0001]
[  146.887360] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[  146.887380] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[  147.015987] Yenta: ISA IRQ mask 0x06b8, PCI irq 0
[  147.016021] Socket status: 30000011
[  147.786664] irda_init()
[  147.786789] NET: Registered protocol family 23
[  147.839701] IrDA: Registered device irda0
[  147.839736] toshoboe: Using multiple tasks, version $Id: donauboe.c V2.18 ven jan 10 03:14:16 2003$
[  150.018630] pccard: PCMCIA card inserted into slot 0
[  150.386574] pccard: PCMCIA card inserted into slot 1
[  151.909500] Real Time Clock Driver v1.12
[  152.539713] Floppy drive(s): fd0 is 1.44M
[  152.548500] input: PC Speaker as /class/input/input1
[  152.555923] FDC 0 is an 8272A
[  152.665192] input: PS/2 Generic Mouse as /class/input/input2
[  154.950927] parport: PnPBIOS parport detected.
[  154.951067] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  155.875423] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x330-0x337 0x388-0x38f
[  155.877233] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[  155.878373] cs: IO port probe 0x820-0x8ff: clean.
[  155.879376] cs: IO port probe 0xc00-0xcf7: clean.
[  155.882305] cs: IO port probe 0xa00-0xaff: clean.
[  155.883376] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[  155.927378] pcmcia: registering new device pcmcia1.0
[  155.938205] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x330-0x337 0x388-0x38f
[  155.940040] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[  155.941137] cs: IO port probe 0x820-0x8ff: clean.
[  155.942194] cs: IO port probe 0xc00-0xcf7: clean.
[  155.944827] cs: IO port probe 0xa00-0xaff: clean.
[  155.945916] cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa00fffff
[  155.955115] pcmcia: registering new device pcmcia0.0
[  157.838059] eth0: 3Com 3c589, io 0x300, irq 3, hw_addr 00:10:5A:FC:7D:29
[  157.838114]   8K FIFO split 5:3 Rx:Tx, auto xcvr
[  158.132515] udev: renamed network interface eth0 to eth1
[  158.579654] airo:  Probing for PCI adapters
[  158.584483] airo:  Finished probing for PCI adapters
[  159.783463] airo: cmd= 111
[  159.783500] airo: status= 7f11
[  159.783515] airo: Rsp0= 2
[  159.783529] airo: Rsp1= 0
[  159.783543] airo: Rsp2= 0
[  159.783563] airo: Doing fast bap_reads
[  159.820658] airo: MAC enabled eth0 0:40:96:36:5c:90
[  159.821583] eth0: index 0x05: Vcc 5.0, Vpp 5.0, irq 4, io 0x0100-0x013f
[  160.275386] NET: Registered protocol family 17
[  160.281092] Setting key 0
[  161.849746] lp0: using parport0 (interrupt-driven).
[  162.210169] fuse init (API version 7.3)
[  162.837076] Adding 465844k swap on /dev/hda5.  Priority:-1 extents:1 across:465844k
[  164.186491] EXT3 FS on hda3, internal journal
[  170.688847] kjournald starting.  Commit interval 5 seconds
[  170.688995] EXT3 FS on hda1, internal journal
[  170.689037] EXT3-fs: mounted filesystem with ordered data mode.
[  170.743198] kjournald starting.  Commit interval 5 seconds
[  170.744208] EXT3 FS on hda8, internal journal
[  170.744253] EXT3-fs: mounted filesystem with ordered data mode.
[  170.776791] kjournald starting.  Commit interval 5 seconds
[  170.776926] EXT3 FS on hda7, internal journal
[  170.776967] EXT3-fs: mounted filesystem with ordered data mode.
[  170.819314] kjournald starting.  Commit interval 5 seconds
[  170.819443] EXT3 FS on hda9, internal journal
[  170.819483] EXT3-fs: mounted filesystem with ordered data mode.
[  170.857161] kjournald starting.  Commit interval 5 seconds
[  170.859209] EXT3 FS on hda4, internal journal
[  170.859252] EXT3-fs: mounted filesystem with ordered data mode.
[  170.915054] kjournald starting.  Commit interval 5 seconds
[  170.916675] EXT3 FS on hda6, internal journal
[  170.916721] EXT3-fs: mounted filesystem with ordered data mode.
[  183.007861] ip_tables: (C) 2000-2002 Netfilter core team
[  201.816943] NET: Registered protocol family 10
[  201.818214] lo: Disabled Privacy Extensions
[  201.820376] IPv6 over IPv4 tunneling driver
[  210.652557] ppdev: user-space parallel port driver
[  211.699294] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[  212.401952] eth0: no IPv6 routers present
[  212.481935] eth1: no IPv6 routers present
[  380.658607] eth1: flipped to 10base2
[  419.653199] eth1: coax cable problem
[  725.695655] Setting key 0
[  735.365377] eth0: no IPv6 routers present


dmesg | tail -24
[  170.776967] EXT3-fs: mounted filesystem with ordered data mode.
[  170.819314] kjournald starting.  Commit interval 5 seconds
[  170.819443] EXT3 FS on hda9, internal journal
[  170.819483] EXT3-fs: mounted filesystem with ordered data mode.
[  170.857161] kjournald starting.  Commit interval 5 seconds
[  170.859209] EXT3 FS on hda4, internal journal
[  170.859252] EXT3-fs: mounted filesystem with ordered data mode.
[  170.915054] kjournald starting.  Commit interval 5 seconds
[  170.916675] EXT3 FS on hda6, internal journal
[  170.916721] EXT3-fs: mounted filesystem with ordered data mode.
[  183.007861] ip_tables: (C) 2000-2002 Netfilter core team
[  201.816943] NET: Registered protocol family 10
[  201.818214] lo: Disabled Privacy Extensions
[  201.820376] IPv6 over IPv4 tunneling driver
[  210.652557] ppdev: user-space parallel port driver
[  211.699294] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[  212.401952] eth0: no IPv6 routers present
[  212.481935] eth1: no IPv6 routers present
[  380.658607] eth1: flipped to 10base2
[  419.653199] eth1: coax cable problem
[  725.695655] Setting key 0
[  735.365377] eth0: no IPv6 routers present
[ 4058.720159] usb 1-1: new full speed USB device using ohci_hcd and address 2
[ 4063.719383] ohci_hcd 0000:00:0b.0: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.


what do you suggest? any improvements?

---

### Post by prshah on 2009-03-21
> **petebarchetta said:**
> [ 4063.719383] ohci_hcd 0000:00:0b.0: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.


Suggestions: (only to be followed at your own risk)

a) Enable Plug'n'Play operating system option in your BIOS
b) Enable "USB keyboard" support option in your BIOS.

---

### Post by petebarchetta on 2009-03-22
> **prshah said:**
> Suggestions: (only to be followed at your own risk)

a) Enable Plug'n'Play operating system option in your BIOS
b) Enable "USB keyboard" support option in your BIOS.

hello,

thanks for the suggestion, would i assue that the irqpoll in the grub file is not allowing the USB side to enable?
i had the issue in ubuntu dapper, but this was solved by inputting noapic and irqpoll into the grub config?
also is there a blacklist for usb as there is in PCMCIA?
i recently had a issue with PCMCIA and this was solved by adding a couple of lines into the wireless.opts file to break the module, and make it rebuild?

A) due to the age of the machine its a p1 MMX i dont think it has PnP as an option, but the OS's that i have installed on the machines have seen the ports and allowed PnP before
b) same as above, although in XP and Linux (dapper) the system saw the usb port, it still does if i use usb mouse, but does not allow usb HD or pendrive though
thanks for your time

---

### Post by petebarchetta on 2009-03-26
note this problem isnt filesystem related as i have tried oth NTFS and Fat32 drives and neither seem to enable, they are visible in the places drop down menue, but when you click on them they come up with unmountable errors

---

### Post by petebarchetta on 2009-03-26
Edit,
it only seems related to Hardy, this machine did run Dapper LTS and went through the upgrade proceedure, rather than clean hardy install, usb access for usb memory sticks worked in dapper.

i can use the USB mouse ( logitech trackman marble) happily with this, but i cant see any issues with the dmesg output shown earlier, anyone got any suggestions as this is a great little workhorse and i'd hate to go back to dapper when hardy is working well apart from not recognising the usb pendrives

---

