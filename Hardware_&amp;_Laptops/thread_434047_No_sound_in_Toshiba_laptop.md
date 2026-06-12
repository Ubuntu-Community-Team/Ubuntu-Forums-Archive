---
title: "No sound in Toshiba laptop"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by jdelasalas on 2007-05-05
I recently purchased a Toshiba A135-S2266, I have gotten everything to work across the board except the sound.

---

### Post by Swankyman on 2007-05-05
Hi,

we need more info to help

attach the result of these commands typed into the terminal:

dmesg
lspci
lsmod

rich

---

### Post by jdelasalas on 2007-05-06
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

---

### Post by jdelasalas on 2007-05-06
wlan_wep                7936  1 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
dev_acpi               12292  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
video                  16388  0 
button                  8720  0 
container               5248  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ac                      6020  0 
sbs                    15652  0 
dock                   10268  0 
i2c_ec                  5888  1 sbs
ipv6                  268704  8 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel          21912  0 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
wlan_scan_sta          14976  1 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ath_rate_sample        14080  1 
pcmcia                 39212  0 
joydev                 10816  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
snd                    54020  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
ath_pci                97312  0 
wlan                  204484  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
pcspkr                  4224  0 
8139cp                 25088  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               9740  0 
ati_agp                10124  0 
agpgart                35400  1 ati_agp
serio_raw               7940  0 
psmouse                38920  0 
ath_hal               192592  3 ath_rate_sample,ath_pci
i2c_core               22784  2 i2c_ec,i2c_piix4
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  6 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
8139too                27648  0 
mii                     6528  2 8139cp,8139too
atiixp                  7440  0 [permanent]
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  3 ehci_hcd,ohci_hcd
sata_sil               12808  2 
ata_generic             9092  0 
libata                125720  2 sata_sil,ata_generic
scsi_mod              142348  3 sg,sd_mod,libata
generic                 5124  0 [permanent]
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by DagMan on 2007-05-07
Maybe this first post or the 8th post from here is worth a shot
[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

---

### Post by jdelasalas on 2007-05-07
There is actually a new development in this story.  For shits and giggles i installed the most recent version of the alsa drivers and now, the volume thing doesn't have an "X" over it.  However, I still can't hear anything, but i can manipulate the volume.

---

### Post by tyler22 on 2007-05-07
read this thread, it has worked for me and many others.

Good luck!

[http://ubuntuforums.org/showthread.php?t=392350&highlight=toshiba]("http://ubuntuforums.org/showthread.php?t=392350&highlight=toshiba")

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

[B][COLOR="Red"]
 lsmod[/COLOR][/B]
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  1 
cpufreq_stats           7360  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
sbs                    15652  0 
ac                      6020  0 
container               5248  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
button                  8720  0 
video                  16388  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
battery                10756  0 
ipv6                  268704  10 
nls_utf8                3072  2 
ntfs                  107764  2 
gameport               16520  0 
ac97_bus                3456  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
joydev                 10816  0 
wlan_scan_sta          14976  1 
ath_rate_sample        14080  1 
pcmcia                 39212  0 
ath_pci                97312  0 
wlan                  204484  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
i2c_piix4               9740  0 
ati_agp                10124  0 
agpgart                35400  1 ati_agp
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               22784  2 i2c_ec,i2c_piix4
serio_raw               7940  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
psmouse                38920  0 
soundcore               8672  0 
pcspkr                  4224  0 
af_packet              23816  6 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  5 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
8139too                27648  0 
generic                 5124  0 [permanent]
sata_sil               12808  4 
atiixp                  7440  0 [permanent]
ata_generic             9092  0 
libata                125720  2 sata_sil,ata_generic
ehci_hcd               34188  0 
scsi_mod              142348  3 sg,sd_mod,libata
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ohci_hcd               22532  0 
usbcore               134280  3 ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability







> **Swankyman said:**
> Hi,

we need more info to help

attach the result of these commands typed into the terminal:

dmesg
lspci
lsmod

rich

---

### Post by adameye on 2007-05-08
**[COLOR="Red"]dmesg[/COLOR]**
 .....
[   13.947287] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
[   13.947314] Total of 2 processors activated (6937.98 BogoMIPS).
[   13.947496] ENABLING IO-APIC IRQs
[   13.947711] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   14.094636] checking TSC synchronization across 2 CPUs: passed.
[    0.003999] Brought up 2 CPUs
[    0.165031] migration_cost=132
[    0.165348] Booting paravirtualized kernel on bare hardware
[    0.165456] Time: 10:04:46  Date: 04/08/107
[    0.165492] NET: Registered protocol family 16
[    0.165592] EISA bus registered
[    0.165600] ACPI: bus type pci registered
[    0.183442] PCI: PCI BIOS revision 2.10 entry at 0xfd5b4, last bus=14
[    0.183445] PCI: Using configuration type 1
[    0.183447] Setting up standard PCI resources
[    0.190910] ACPI Error (evregion-0317): No handler for Region [ERAM] (da0f0484) [EmbeddedControl] [20060707]
[    0.190917] ACPI Error (exfldio-0290): Region EmbeddedControl(3) has no handler [20060707]
[    0.190922] ACPI Exception (dswexec-0458): AE_NOT_EXIST, While resolving operands for [OpcodeName unavailable] [20060707]
[    0.190928] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.HTEV] (Node da0e8e8c), AE_NOT_EXIST
[    0.190963] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node da0f1f2c), AE_NOT_EXIST
[    0.192687] APIC error on CPU1: 00(40)
[    0.201291] ACPI: Interpreter enabled
[    0.201296] ACPI: Using IOAPIC for interrupt routing
[    0.203170] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.203180] PCI: Probing PCI hardware (bus 00)
[    0.206014] Boot video device is 0000:01:05.0
[    0.206631] PCI: Transparent bridge - 0000:00:14.4
[    0.206812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.212051] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.220061] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.220647] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.221220] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.221797] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.222378] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.222952] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.223529] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.224171] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.224755] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[    0.267912] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.268983] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.270389] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.270407] pnp: PnP ACPI init
[    0.295973] pnp: PnP ACPI: found 10 devices
[    0.295981] PnPBIOS: Disabled by ACPI PNP
[    0.296070] PCI: Using ACPI for IRQ routing
[    0.296076] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.332842] NET: Registered protocol family 8
[    0.332847] NET: Registered protocol family 20
[    0.333306] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.333313] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[    0.333319] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[    0.333324] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.333905] PCI: Bridge: 0000:00:01.0
[    0.333910]   IO window: 9000-9fff
[    0.333918]   MEM window: d0000000-d00fffff
[    0.333925]   PREFETCH window: d8000000-dfffffff
[    0.333932] PCI: Bridge: 0000:00:06.0
[    0.333935]   IO window: disabled.
[    0.333943]   MEM window: d0100000-d01fffff
[    0.333948]   PREFETCH window: disabled.
[    0.333971] PCI: Bus 10, cardbus bridge: 0000:09:04.0
[    0.333975]   IO window: 0000a400-0000a4ff
[    0.333985]   IO window: 0000a800-0000a8ff
[    0.333994]   PREFETCH window: 24000000-27ffffff
[    0.334004]   MEM window: 28000000-2bffffff
[    0.334013] PCI: Bridge: 0000:00:14.4
[    0.334019]   IO window: a000-afff
[    0.334030]   MEM window: f0200000-f02fffff
[    0.334039]   PREFETCH window: f0300000-f03fffff
[    0.334076] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.334117] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.334183] NET: Registered protocol family 2
[    0.367692] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.367852] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.368046] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.368146] TCP: Hash tables configured (established 16384 bind 8192)
[    0.368151] TCP reno registered
[    0.379798] checking if image is initramfs... it is
[    1.803503] Freeing initrd memory: 7006k freed
[    1.804802] audit: initializing netlink socket (disabled)
[    1.804835] audit(1178618686.592:1): initialized
[    1.805175] VFS: Disk quotas dquot_6.5.1
[    1.805219] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.805315] io scheduler noop registered
[    1.805321] io scheduler anticipatory registered
[    1.805326] io scheduler deadline registered
[    1.805350] io scheduler cfq registered (default)
[    1.805709] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    1.805766] assign_interrupt_mode Found MSI capability
[    1.805773] Allocate Port Service[0000:00:06.0:pcie00]
[    1.805849] Allocate Port Service[0000:00:06.0:pcie02]
[    1.806166] isapnp: Scanning for PnP cards...
[    2.163211] isapnp: No Plug & Play device found
[    2.213975] Real Time Clock Driver v1.12ac
[    2.214101] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    2.215414] mice: PS/2 mouse device common for all mice
[    2.216585] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.216896] input: Macintosh mouse button emulation as /class/input/input0
[    2.216971] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    2.216978] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    2.217422] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.217874] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.217970] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.217979] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.217985] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.217991] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.217996] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.218181] EISA: Probing bus 0 at eisa.0
[    2.218200] Cannot allocate resource for EISA slot 1
[    2.218243] Cannot allocate resource for EISA slot 8
[    2.218247] EISA: Detected 0 cards.
[    2.237481] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.248401] TCP cubic registered
[    2.248417] NET: Registered protocol family 1
[    2.248461] Starting balanced_irq
[    2.248474] Using IPI No-Shortcut mode
[    2.248595] ACPI: (supports S0 S3 S4 S5)
[    2.248692]   Magic number: 7:166:72
[    2.249270] Time: tsc clocksource has been installed.
[    2.249426] Freeing unused kernel memory: 328k freed
[    3.643505] Capability LSM initialized
[    3.719200] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    3.720682] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    3.721318] ACPI: CPU0 (power states: C1[C1] C3[C3])
[    3.721328] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.722593] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    3.723186] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.723868] ACPI: CPU1 (power states: C1[C1] C3[C3])
[    3.723878] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.723893] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.723908] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.723924] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.723938] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.723951] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.723965] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    4.387140] usbcore: registered new interface driver usbfs
[    4.387189] usbcore: registered new interface driver hub
[    4.387236] usbcore: registered new device driver usb
[    4.388912] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.388986] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[    4.389014] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.389253] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    4.389291] ohci_hcd 0000:00:13.0: irq 17, io mem 0xd0504000
[    4.427171] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.438011] SCSI subsystem initialized
[    4.451783] libata version 2.20 loaded.
[    4.454875] usb usb1: configuration #1 chosen from 1 choice
[    4.454937] hub 1-0:1.0: USB hub found
[    4.454960] hub 1-0:1.0: 4 ports detected
[    4.559471] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[    4.559503] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.559739] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    4.559768] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd0505000
[    4.614634] usb usb2: configuration #1 chosen from 1 choice
[    4.614691] hub 2-0:1.0: USB hub found
[    4.614713] hub 2-0:1.0: 4 ports detected
[    4.718537] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[    4.718568] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.718619] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    4.718692] ehci_hcd 0000:00:13.2: irq 17, io mem 0xd0506000
[    4.718709] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.718858] usb usb3: configuration #1 chosen from 1 choice
[    4.718912] hub 3-0:1.0: USB hub found
[    4.718925] hub 3-0:1.0: 8 ports detected
[    4.825443] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.825478] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[    4.825499] ATIIXP: chipset revision 128
[    4.825503] ATIIXP: not 100% native mode: will probe irqs later
[    4.825522]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
[    4.825541] Probing IDE interface ide1...
[    5.561719] hdc: HL-DT-ST DVDRAM GMA-4082N, ATAPI CD/DVD-ROM drive
[    6.384000] Time: acpi_pm clocksource has been installed.
[    6.508000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.512000] sata_sil 0000:00:12.0: version 2.2
[    6.512000] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[    6.512000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 19
[    6.512000] ata1: SATA max UDMA/100 cmd 0xdc8ae080 ctl 0xdc8ae08a bmdma 0xdc8ae000 irq 19
[    6.512000] ata2: SATA max UDMA/100 cmd 0xdc8ae0c0 ctl 0xdc8ae0ca bmdma 0xdc8ae008 irq 19
[    6.512000] scsi0 : sata_sil
[    6.980000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.988000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    6.988000] ata1.00: ATA-8: FUJITSU MHW2080BH, 00000012, max UDMA/100
[    6.988000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.996000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    6.996000] ata1.00: configured for UDMA/100
[    6.996000] scsi1 : sata_sil
[    7.308000] ata2: SATA link down (SStatus 0 SControl 300)
[    7.308000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0000 PQ: 0 ANSI: 5
[    7.308000] 8139cp 0000:09:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    7.308000] 8139cp 0000:09:06.0: Try the "8139too" driver instead.
[    7.316000] 8139too Fast Ethernet driver 0.9.28
[    7.320000] ACPI: PCI Interrupt 0000:09:06.0[A] -> GSI 22 (level, low) -> IRQ 19
[    7.320000] eth0: RealTek RTL8139 at 0xdc888000, 00:16:d4:97:63:83, IRQ 19
[    7.320000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    7.328000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.328000] Uniform CD-ROM driver Revision: 3.20
[    7.332000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    7.332000] sda: Write Protect is off
[    7.332000] sda: Mode Sense: 00 3a 00 00
[    7.332000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.332000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    7.332000] sda: Write Protect is off
[    7.332000] sda: Mode Sense: 00 3a 00 00
[    7.332000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.332000]  sda: sda1 sda2 sda3 sda4
[    7.404000] sd 0:0:0:0: Attached scsi disk sda
[    7.408000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.792000] Attempting manual resume
[    7.792000] swsusp: Resume From Partition 8:4
[    7.792000] PM: Checking swsusp image.
[    7.792000] PM: Resume from disk failed.
[    7.824000] kjournald starting.  Commit interval 5 seconds
[    7.824000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.156000] eth0: link down
[   19.440000] NET: Registered protocol family 17
[   20.192000] input: PC Speaker as /class/input/input2
[   20.488000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.508000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.564000] Yenta: CardBus bridge found at 0000:09:04.0 [1179:ff00]
[   20.564000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.564000] Yenta: Routing CardBus interrupts to PCI
[   20.564000] Yenta TI: socket 0000:09:04.0, mfunc 0x00111c12, devctl 0x44
[   20.676000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.772000] ath_hal: module license 'Proprietary' taints kernel.
[   20.780000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   20.796000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 16
[   20.796000] Socket status: 30000006
[   20.796000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   20.796000] cs: IO port probe 0xa000-0xafff: clean.
[   20.796000] pcmcia: parent PCI bridge Memory window: 0xf0200000 - 0xf02fffff
[   20.796000] pcmcia: parent PCI bridge Memory window: 0xf0300000 - 0xf03fffff
[   20.796000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   20.880000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   20.880000] synaptics: Toshiba Satellite A135 detected, limiting rate to 40pps.
[   20.908000] wlan: 0.8.4.2 (0.9.3)
[   20.912000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   20.940000] ath_pci: 0.9.4.5 (0.9.3)
[   20.940000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 20
[   20.940000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   21.480000] ath_rate_sample: 1.2 (0.9.3)
[   21.480000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   21.480000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   21.480000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   21.480000] wifi0: mac 10.0 phy 6.1 radio 10.2
[   21.480000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   21.480000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   21.480000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   21.480000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   21.480000] wifi0: Use hw queue 8 for CAB traffic
[   21.480000] wifi0: Use hw queue 9 for beacons
[   21.504000] wifi0: Atheros 5424/2424: mem=0xd0100000, irq=20
[   21.696000] cs: IO port probe 0x100-0x3af: clean.
[   21.720000] cs: IO port probe 0x3e0-0x4ff: clean.
[   21.720000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   21.720000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   21.720000] cs: IO port probe 0xa00-0xaff: clean.
[   21.872000] fuse init (API version 7.8)
[   21.968000] lp: driver loaded but no devices found
[   22.168000] Adding 489972k swap on /dev/disk/by-uuid/c99ad3ea-74c5-43b3-8f0d-02da58769809.  Priority:-1 extents:1 across:489972k
[   22.328000] EXT3 FS on sda3, internal journal
[   22.604000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   22.680000] NTFS volume version 3.1.
[   22.728000] NTFS volume version 3.1.
[   24.592000] NET: Registered protocol family 10
[   24.592000] lo: Disabled Privacy Extensions
[   24.592000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.880000] ACPI: Battery Slot [BAT1] (battery present)
[   27.912000] No dock devices found.
[   27.992000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   28.024000] input: Power Button (FF) as /class/input/input4
[   28.024000] ACPI: Power Button (FF) [PWRF]
[   28.024000] input: Lid Switch as /class/input/input5
[   28.024000] ACPI: Lid Switch [LID]
[   28.024000] input: Power Button (CM) as /class/input/input6
[   28.024000] ACPI: Power Button (CM) [PWRB]
[   28.272000] ibm_acpi: ec object not found
[   28.340000] ACPI: AC Adapter [ACAD] (on-line)
[   28.472000] Using specific hotkey driver
[   28.544000] pcc_acpi: loading...
[   34.456000] ppdev: user-space parallel port driver
[   34.740000] ath0: no IPv6 routers present
[   35.144000] apm: BIOS not found.
[   35.284000] Bluetooth: Core ver 2.11
[   35.284000] NET: Registered protocol family 31
[   35.284000] Bluetooth: HCI device and connection manager initialized
[   35.284000] Bluetooth: HCI socket layer initialized
[   35.296000] Bluetooth: L2CAP ver 2.8
[   35.296000] Bluetooth: L2CAP socket layer initialized
[   35.536000] Bluetooth: RFCOMM socket layer initialized
[   35.536000] Bluetooth: RFCOMM TTY layer initialized
[   35.536000] Bluetooth: RFCOMM ver 1.8

---

### Post by spadge63 on 2007-05-12
[   14.558146] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[   14.558151] monitor/mwait feature present.
[   14.558156] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.558158] CPU: L2 cache: 1024K
[   14.558161] CPU: Physical Processor ID: 0
[   14.558162] CPU: Processor Core ID: 1
[   14.558164] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
[   14.558579] CPU1: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[   14.558607] Total of 2 processors activated (6404.47 BogoMIPS).
[   14.558790] ENABLING IO-APIC IRQs
[   14.559009] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   14.705937] checking TSC synchronization across 2 CPUs: passed.
[    0.003991] Brought up 2 CPUs
[    0.164753] migration_cost=125
[    0.165084] Booting paravirtualized kernel on bare hardware
[    0.165193] Time: 18:20:20  Date: 04/12/107
[    0.165233] NET: Registered protocol family 16
[    0.165336] EISA bus registered
[    0.165344] ACPI: bus type pci registered
[    0.182897] PCI: PCI BIOS revision 2.10 entry at 0xfd5b4, last bus=14
[    0.182900] PCI: Using configuration type 1
[    0.182902] Setting up standard PCI resources
[    0.191143] ACPI Error (evregion-0317): No handler for Region [ERAM] (da0ec484) [EmbeddedControl] [20060707]
[    0.191151] ACPI Error (exfldio-0290): Region EmbeddedControl(3) has no handler [20060707]
[    0.191157] ACPI Exception (dswexec-0458): AE_NOT_EXIST, While resolving operands for [OpcodeName unavailable] [20060707]
[    0.191163] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.HTEV] (Node da0e4e8c), AE_NOT_EXIST
[    0.191201] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node da0edf2c), AE_NOT_EXIST
[    0.203655] ACPI: Interpreter enabled
[    0.203660] ACPI: Using IOAPIC for interrupt routing
[    0.205540] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.205550] PCI: Probing PCI hardware (bus 00)
[    0.208379] Boot video device is 0000:01:05.0
[    0.208994] PCI: Transparent bridge - 0000:00:14.4
[    0.209174] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.214417] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.222553] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.223139] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.223726] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.224302] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.224882] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.225455] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.226032] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.226616] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.227197] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[    0.267825] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.268897] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.270301] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.270318] pnp: PnP ACPI init
[    0.295878] pnp: PnP ACPI: found 10 devices
[    0.295886] PnPBIOS: Disabled by ACPI PNP
[    0.295971] PCI: Using ACPI for IRQ routing
[    0.295977] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.332743] NET: Registered protocol family 8
[    0.332747] NET: Registered protocol family 20
[    0.333200] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.333207] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[    0.333213] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[    0.333218] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.333798] PCI: Bridge: 0000:00:01.0
[    0.333804]   IO window: 9000-9fff
[    0.333812]   MEM window: d0000000-d00fffff
[    0.333819]   PREFETCH window: d8000000-dfffffff
[    0.333826] PCI: Bridge: 0000:00:06.0
[    0.333829]   IO window: disabled.
[    0.333837]   MEM window: d0100000-d01fffff
[    0.333842]   PREFETCH window: disabled.
[    0.333865] PCI: Bus 10, cardbus bridge: 0000:09:04.0
[    0.333869]   IO window: 0000a400-0000a4ff
[    0.333879]   IO window: 0000a800-0000a8ff
[    0.333888]   PREFETCH window: 24000000-27ffffff
[    0.333898]   MEM window: 28000000-2bffffff
[    0.333907] PCI: Bridge: 0000:00:14.4
[    0.333913]   IO window: a000-afff
[    0.333924]   MEM window: f0200000-f02fffff
[    0.333933]   PREFETCH window: f0300000-f03fffff
[    0.333969] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.334011] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.334074] NET: Registered protocol family 2
[    0.367580] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.367740] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.367934] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.368033] TCP: Hash tables configured (established 16384 bind 8192)
[    0.368038] TCP reno registered
[    0.379674] checking if image is initramfs... it is
[    1.799079] Freeing initrd memory: 6987k freed
[    1.800371] audit: initializing netlink socket (disabled)
[    1.800406] audit(1178994020.616:1): initialized
[    1.800759] VFS: Disk quotas dquot_6.5.1
[    1.800802] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.800900] io scheduler noop registered
[    1.800906] io scheduler anticipatory registered
[    1.800911] io scheduler deadline registered
[    1.800935] io scheduler cfq registered (default)
[    1.801291] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    1.801366] assign_interrupt_mode Found MSI capability
[    1.801372] Allocate Port Service[0000:00:06.0:pcie00]
[    1.801449] Allocate Port Service[0000:00:06.0:pcie02]
[    1.801752] isapnp: Scanning for PnP cards...
[    2.158425] isapnp: No Plug & Play device found
[    2.208481] Real Time Clock Driver v1.12ac
[    2.208607] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    2.209941] mice: PS/2 mouse device common for all mice
[    2.211119] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.211430] input: Macintosh mouse button emulation as /class/input/input0
[    2.211506] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    2.211513] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    2.211949] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.212280] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.212375] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.212384] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.212390] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.212396] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.212401] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.212599] EISA: Probing bus 0 at eisa.0
[    2.212617] Cannot allocate resource for EISA slot 1
[    2.212661] Cannot allocate resource for EISA slot 8
[    2.212665] EISA: Detected 0 cards.
[    2.242823] TCP cubic registered
[    2.242841] NET: Registered protocol family 1
[    2.242885] Starting balanced_irq
[    2.242898] Using IPI No-Shortcut mode
[    2.243068] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.243164] ACPI: (supports S0 S3 S4 S5)
[    2.243291]   Magic number: 7:76:342
[    2.244049] Freeing unused kernel memory: 328k freed
[    2.244687] Time: tsc clocksource has been installed.
[    3.648754] Capability LSM initialized
[    3.727890] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    3.729352] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    3.729986] ACPI: CPU0 (power states: C1[C1] C3[C3])
[    3.729996] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.731284] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    3.731878] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.732548] ACPI: CPU1 (power states: C1[C1] C3[C3])
[    3.732558] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.732573] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.732588] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.732605] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.732619] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.732632] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.732646] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    4.343115] usbcore: registered new interface driver usbfs
[    4.343169] usbcore: registered new interface driver hub
[    4.343215] usbcore: registered new device driver usb
[    4.344776] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.344836] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[    4.344859] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.345054] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    4.345088] ohci_hcd 0000:00:13.0: irq 17, io mem 0xd0504000
[    4.410055] usb usb1: configuration #1 chosen from 1 choice
[    4.410111] hub 1-0:1.0: USB hub found
[    4.410138] hub 1-0:1.0: 4 ports detected
[    4.440165] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.514362] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[    4.514395] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.514443] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    4.514517] ehci_hcd 0000:00:13.2: irq 17, io mem 0xd0506000
[    4.514534] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.514679] usb usb2: configuration #1 chosen from 1 choice
[    4.514736] hub 2-0:1.0: USB hub found
[    4.514750] hub 2-0:1.0: 8 ports detected
[    4.621397] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[    4.621428] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.621504] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    4.621538] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd0505000
[    4.632771] SCSI subsystem initialized
[    4.645160] libata version 2.20 loaded.
[    4.677332] usb usb3: configuration #1 chosen from 1 choice
[    4.677393] hub 3-0:1.0: USB hub found
[    4.677415] hub 3-0:1.0: 4 ports detected
[    4.781161] 8139cp 0000:09:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.781170] 8139cp 0000:09:06.0: Try the "8139too" driver instead.
[    4.782635] sata_sil 0000:00:12.0: version 2.2
[    4.782674] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[    4.782692] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[    4.782820] ata1: SATA max UDMA/100 cmd 0xdc868080 ctl 0xdc86808a bmdma 0xdc868000 irq 18
[    4.782878] ata2: SATA max UDMA/100 cmd 0xdc8680c0 ctl 0xdc8680ca bmdma 0xdc868008 irq 18
[    4.782903] scsi0 : sata_sil
[    4.784142] 8139too Fast Ethernet driver 0.9.28
[    5.248305] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.256954] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.256966] ata1.00: ATA-8: FUJITSU MHW2080BH, 00000012, max UDMA/100
[    5.256973] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.264945] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.264954] ata1.00: configured for UDMA/100
[    5.264978] scsi1 : sata_sil
[    5.575791] ata2: SATA link down (SStatus 0 SControl 300)
[    5.576040] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0000 PQ: 0 ANSI: 5
[    5.576865] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    5.576898] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[    5.576919] ATIIXP: chipset revision 128
[    5.576923] ATIIXP: not 100% native mode: will probe irqs later
[    5.576941]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
[    5.576961] Probing IDE interface ide1...
[    6.472000] Time: acpi_pm clocksource has been installed.
[    6.952000] hdc: MATSHITADVD-RAM UJ-850S, ATAPI CD/DVD-ROM drive
[    7.288000] ide1 at 0x170-0x177,0x376 on irq 15
[    7.300000] ACPI: PCI Interrupt 0000:09:06.0[A] -> GSI 22 (level, low) -> IRQ 18
[    7.300000] eth0: RealTek RTL8139 at 0xdc866000, 00:16:d4:91:57:73, IRQ 18
[    7.300000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    7.312000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    7.312000] sda: Write Protect is off
[    7.312000] sda: Mode Sense: 00 3a 00 00
[    7.312000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.312000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    7.312000] sda: Write Protect is off
[    7.312000] sda: Mode Sense: 00 3a 00 00
[    7.312000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.312000]  sda: sda1 sda2 <<6>hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.320000] Uniform CD-ROM driver Revision: 3.20
[    7.372000]  sda5 >
[    7.372000] sd 0:0:0:0: Attached scsi disk sda
[    7.380000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.624000] Attempting manual resume
[    7.624000] swsusp: Resume From Partition 8:5
[    7.624000] PM: Checking swsusp image.
[    7.624000] PM: Resume from disk failed.
[    7.652000] kjournald starting.  Commit interval 5 seconds
[    7.652000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   19.300000] NET: Registered protocol family 17
[   19.824000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.848000] shpchp: Unknown symbol acpi_run_oshp
[   19.848000] shpchp: Unknown symbol pci_hp_change_slot_info
[   19.848000] shpchp: Unknown symbol pci_hp_register
[   19.848000] shpchp: Unknown symbol pci_hp_deregister
[   19.848000] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[   20.212000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.220000] input: PC Speaker as /class/input/input2
[   20.240000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.324000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   20.376000] Yenta: CardBus bridge found at 0000:09:04.0 [1179:ff00]
[   20.376000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.376000] Yenta: Routing CardBus interrupts to PCI
[   20.376000] Yenta TI: socket 0000:09:04.0, mfunc 0x00111c12, devctl 0x44
[   20.496000] ath_hal: module license 'Proprietary' taints kernel.
[   20.496000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   20.608000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 16
[   20.608000] Socket status: 30000006
[   20.608000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   20.608000] cs: IO port probe 0xa000-0xafff: clean.
[   20.608000] pcmcia: parent PCI bridge Memory window: 0xf0200000 - 0xf02fffff
[   20.608000] pcmcia: parent PCI bridge Memory window: 0xf0300000 - 0xf03fffff
[   20.740000] wlan: 0.8.4.2 (0.9.3)
[   20.768000] ath_pci: 0.9.4.5 (0.9.3)
[   20.768000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 20
[   20.768000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   20.800000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   20.800000] synaptics: Toshiba Satellite A135 detected, limiting rate to 40pps.
[   21.224000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   21.336000] ath_rate_sample: 1.2 (0.9.3)
[   21.340000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   21.340000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   21.340000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   21.340000] wifi0: mac 10.0 phy 6.1 radio 10.2
[   21.340000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   21.340000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   21.340000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   21.340000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   21.340000] wifi0: Use hw queue 8 for CAB traffic
[   21.340000] wifi0: Use hw queue 9 for beacons
[   21.360000] wifi0: Atheros 5424/2424: mem=0xd0100000, irq=20
[   21.576000] cs: IO port probe 0x100-0x3af: clean.
[   21.604000] cs: IO port probe 0x3e0-0x4ff: clean.
[   21.604000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   21.604000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   21.604000] cs: IO port probe 0xa00-0xaff: clean.
[   21.672000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 19
[   22.388000] si3054: cannot initialize. EXT MID = 0000
[   22.580000] fuse init (API version 7.8)
[   22.668000] lp: driver loaded but no devices found
[   22.724000] Adding 1309256k swap on /dev/disk/by-uuid/1866434d-edc4-4b8f-962f-32d6c398746e.  Priority:-1 extents:1 across:1309256k
[   22.892000] EXT3 FS on sda1, internal journal
[   23.128000] NET: Registered protocol family 10
[   23.128000] lo: Disabled Privacy Extensions
[   28.296000] ACPI: AC Adapter [ACAD] (on-line)
[   28.376000] input: Power Button (FF) as /class/input/input4
[   28.376000] ACPI: Power Button (FF) [PWRF]
[   28.376000] input: Lid Switch as /class/input/input5
[   28.376000] ACPI: Lid Switch [LID]
[   28.400000] input: Power Button (CM) as /class/input/input6
[   28.400000] ACPI: Power Button (CM) [PWRB]
[   28.476000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   28.620000] Using specific hotkey driver
[   28.736000] ibm_acpi: ec object not found
[   28.836000] ACPI: Battery Slot [BAT1] (battery present)
[   28.916000] No dock devices found.
[   28.980000] pcc_acpi: loading...
[   35.136000] ppdev: user-space parallel port driver
[   35.220000] [fglrx] Maximum main memory to use for locked dma buffers: 371 MBytes.
[   35.220000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   35.324000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[   35.996000] apm: BIOS not found.
[   36.260000] Bluetooth: Core ver 2.11
[   36.260000] NET: Registered protocol family 31
[   36.260000] Bluetooth: HCI device and connection manager initialized
[   36.260000] Bluetooth: HCI socket layer initialized
[   36.288000] Bluetooth: L2CAP ver 2.8
[   36.288000] Bluetooth: L2CAP socket layer initialized
[   36.428000] Bluetooth: RFCOMM socket layer initialized
[   36.428000] Bluetooth: RFCOMM TTY layer initialized
[   36.428000] Bluetooth: RFCOMM ver 1.8
[   36.948000] [fglrx] total      GART = 130023424
[   36.948000] [fglrx] free       GART = 114032640
[   36.948000] [fglrx] max single GART = 114032640
[   36.948000] [fglrx] total      LFB  = 67108864
[   36.948000] [fglrx] free       LFB  = 52719616
[   36.948000] [fglrx] max single LFB  = 52719616
[   36.948000] [fglrx] total      Inv  = 0
[   36.948000] [fglrx] free       Inv  = 0
[   36.948000] [fglrx] max single Inv  = 0
[   36.948000] [fglrx] total      TIM  = 0
[   50.588000] eth0: no IPv6 routers present
mike@mike-laptop:~$ lspci
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
mike@mike-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
fglrx                 540004  11 
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
dock                   10268  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
container               5248  0 
video                  16388  0 
button                  8720  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
ac                      6020  0 
ipv6                  268704  10 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel          21912  0 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
joydev                 10816  0 
snd_seq_oss            32896  0 
wlan_scan_sta          14976  1 
snd_seq_midi            9600  0 
ath_rate_sample        14080  1 
snd_rawmidi            25472  1 snd_seq_midi
pcmcia                 39212  0 
ath_pci                97312  0 
wlan                  204484  4 wlan_scan_sta,ath_rate_sample,ath_pci
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_hal               192592  3 ath_rate_sample,ath_pci
yenta_socket           27532  1 
snd                    54020  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
i2c_piix4               9740  0 
ati_agp                10124  0 
agpgart                35400  2 fglrx,ati_agp
psmouse                38920  0 
pcspkr                  4224  0 
shpchp                 34324  0 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               22784  2 i2c_ec,i2c_piix4
pci_hotplug            32576  1 shpchp
serio_raw               7940  0 
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
af_packet              23816  6 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
sd_mod                 23428  3 
ata_generic             9092  0 
8139too                27648  0 
sata_sil               12808  2 
libata                125720  2 ata_generic,sata_sil
scsi_mod              142348  3 sg,sd_mod,libata
atiixp                  7440  0 [permanent]
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  3 ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
mike@mike-laptop:~$

---

### Post by lisati on 2007-06-30
"no sound" seems to be a common challenge on Toshiba laptops - there are a number of threads dealing with this. After a "clean" install of Ubuntu 7.04 on my A100-series laptop, I, too, had no sound. The solution for me was quite simple - use the update manager to get the latest drivers, do a restart, then set the volume control.

If there are updates available, you might notice an orange icon on the menu line. Click on that. If it's not there, try System->Administration->Update manager. You'll need a working internet connection for this to work.

Hope this helps.

---

