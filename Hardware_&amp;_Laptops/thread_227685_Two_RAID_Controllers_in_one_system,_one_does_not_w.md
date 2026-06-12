---
title: "Two RAID Controllers in one system, one does not work"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by Phasmagon on 2006-08-02
Hello everybody I accidentally posted this tread to desktop support so I re-post here.

I recently decided to install Dapper on my primary desktop computer.
On this system dapper installed flawlessly and almost every little bit ran perfectly.

The problem that I am facing begins from the fact that I have three hard drives and three optical drives. One of the hard drives is connected to IDE 1 (primary), one optical drive to IDE 1 (slave), two optical drives are connected to IDE 2, one hard drive is connected to the on board SATA controller and the fourth drive to the IDE channel of an added RAID controller (PCI card).

The problem is that the third drive (the one connected to the PCI card), is not detected. I have tried all hd* combinations, as well as sd*. I suspect that the problem rises from the fact that both on-board SATA controller and PCI RAID controller have the same chipset and as such they are suppoted by the same driver. So I guess there is a conflict there. But I could be wrong. I have used the same controller in the past and I know it is supported in linux. I just want to state that Windows recognize both controllers and can access that drive.

I include relative parts of my lspci and lshw and everything from lsmod


**lspci**
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0d.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 50)
0000:00:0d.1 RAID bus controller: VIA Technologies, Inc. VIA VT6420 (ATA133) Controller (rev 80)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]

**lshw**
        *-storage:0
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: d
             bus info: pci@00:0d.0
             logical name: scsi0
             logical name: scsi1
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list scsi-host
             configuration: driver=sata_via
             resources: ioport:d400-d407 ioport:d000-d003 ioport:b800-b807 ioport:b400-b403 ioport:b000-b00f ioport:a800-a8ff irq:169
        *-storage:1
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@00:0f.0
             logical name: scsi2
             logical name: scsi3
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list emulated scsi-host
             configuration: driver=sata_via
             resources: ioport:8800-8807 ioport:8400-8403 ioport:8000-8007 ioport:7800-7803 ioport:7400-740f ioport:7000-70ff irq:177
           *-disk
                description: SCSI Disk
                product: WDC WD1200JD-00H
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 08.0
                serial: WD-WCALA1088867
                size: 111GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 110GB
                   capabilities: primary
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 1474MB
                   capabilities: primary nofs
        *-storage:2 UNCLAIMED
             description: RAID bus controller
             product: VIA VT6420 (ATA133) Controller
             vendor: VIA Technologies, Inc.
             physical id: d.1
             bus info: pci@00:0d.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list
             resources: ioport:a400-a407 ioport:a000-a003 ioport:9800-9807 ioport:9400-9403 ioport:9000-900f irq:3
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:6800-680f irq:177
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: Maxtor 90871U2
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: FA570480
                   serial: E21B5PKC
                   size: 8297MB
                   capacity: 8297MB
                   capabilities: ata dma lba iordy smart pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
                 *-volume
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 8283MB
                      capabilities: primary bootable
              *-cdrom
                   description: DVD writer
                   product: _NEC DVD_RW ND-2510A
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 2.15
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdb
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: DVD reader
                   product: ASUS DVD-ROM DVD-E616P 0104
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: E1.04
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio dvd
                   configuration: mode=udma4
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
              *-cdrom:1
                   description: CD-R/CD-RW writer
                   product: ASUS CRW-5224A
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 1.36
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list

**lsmod**
binfmt_misc            13192  1
nls_cp437               6208  1
ntfs                  114288  1
rfcomm                 44244  0
l2cap                  29184  5 rfcomm
bluetooth              54244  4 rfcomm,l2cap
ppdev                  10052  0
ipv6                  287456  20
cpufreq_userspace       6816  0
cpufreq_stats           6912  0
freq_table              5152  1 cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        8104  0
cpufreq_conservative     9256  0
video                  16644  0
tc1100_wmi              7172  0
sony_acpi               5900  0
pcc_acpi               12736  0
hotkey                 11812  0
dev_acpi               11652  0
container               4928  0
button                  6992  0
acpi_sbs               20556  0
battery                10308  1 acpi_sbs
ac                      5508  1 acpi_sbs
i2c_acpi_ec             5440  1 acpi_sbs
af_packet              25224  2
dm_mod                 63640  1
md_mod                 76244  0
lp                     12612  0
snd_seq_dummy           4164  0
snd_seq_oss            37632  0
snd_seq_midi            9888  0
snd_seq_midi_event      8064  2 snd_seq_oss,snd_seq_midi
snd_seq                58832  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tsdev                   8320  0
floppy                 65924  0
usbhid                 42912  0
snd_via82xx            31192  1
snd_ac97_codec         99296  1 snd_via82xx
snd_ac97_bus            2688  1 snd_ac97_codec
snd_pcm_oss            56352  0
snd_mixer_oss          20800  1 snd_pcm_oss
snd_mpu401              7112  0
snd_pcm                96772  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              27204  2 snd_seq,snd_pcm
snd_page_alloc         11592  2 snd_via82xx,snd_pcm
snd_mpu401_uart         8896  2 snd_via82xx,snd_mpu401
snd_rawmidi            27552  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9548  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    60068  14 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              11040  1 snd
analog                 12960  0
gameport               17032  2 snd_via82xx,analog
pl2303                 22020  0
psmouse                40132  0
i2c_viapro              9364  0
ftdi_sio               32648  0
usbserial              33448  2 pl2303,ftdi_sio
pcspkr                  2564  0
parport_pc             38340  1
parport                39560  3 ppdev,lp,parport_pc
nvidia               4553140  0
i2c_core               23168  3 i2c_acpi_ec,i2c_viapro,nvidia
serio_raw               8132  0
via_agp                10560  1
agpgart                37072  2 nvidia,via_agp
e100                   42180  0
mii                     6528  1 e100
shpchp                 49312  0
pci_hotplug            30916  1 shpchp
sg                     40352  0
evdev                  10432  3
ext3                  148296  1
jbd                    65684  1 ext3
ide_generic             1792  0
ehci_hcd               36104  0
uhci_hcd               35472  0
usbcore               138948  7 usbhid,pl2303,ftdi_sio,usbserial,ehci_hcd,uhci_hcd
ide_cd                 36228  0
cdrom                  41504  1 ide_cd
ide_disk               19520  2
via82cxxx               9988  0 [permanent]
generic                 5444  0
sd_mod                 20864  3
sata_via               10628  4
libata                 84176  1 sata_via
scsi_mod              145736  3 sg,sd_mod,libata
thermal                14088  0
processor              26696  1 thermal
fan                     5124  0
capability              5256  0
commoncap               7616  1 capability
vesafb                  8924  1
fbcon                  44640  72
tileblit                3072  1 fbcon
font                    8640  1 fbcon
bitblit                 6592  1 fbcon
softcursor              2752  1 bitblit


Any help will be grately appreciated.
Thanks

---

