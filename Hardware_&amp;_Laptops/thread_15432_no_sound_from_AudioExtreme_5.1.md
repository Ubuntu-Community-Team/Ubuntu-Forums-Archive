---
title: "no sound from AudioExtreme 5.1"
date: 2005-02-14
forum: Hardware &amp; Laptops
---

### Post by jamaas on 2005-02-14
Can anyone tell me how to diagnose a problem with a new sound card.

The CD player works, and the volume control gives me two mixers, a CMedia PCI and a CMedia PCI CMI8738-M6 Alsa mixer, when I turn off all the mute buttons still no sound!

I'll stick in my lsmod but would appreciate any suggestions.

Thanks

Jim

jamaas@jamdesktop:/usr/src/linux $ lsmod
Module                  Size  Used by
snd_seq_oss            33536  0
snd_seq_midi_event      7552  1 snd_seq_oss
snd_seq                52176  4 snd_seq_oss,snd_seq_midi_event
snd_pcm_oss            52968  0
snd_mixer_oss          19456  2 snd_pcm_oss
snd_sb16_dsp           11360  0
snd_sb16_csp           20448  0
snd_sb_common          15520  2 snd_sb16_dsp,snd_sb16_csp
proc_intf               3776  0
freq_table              4196  0
cpufreq_userspace       5240  0
cpufreq_powersave       1728  0
button                  6584  0
ac                      4812  0
battery                 9388  0
ipv6                  257028  8
af_packet              22088  2
e100                   31584  0
mii                     5056  1 e100
snd_cmipci             32772  4
snd_pcm                95140  3 snd_pcm_oss,snd_sb16_dsp,snd_cmipci
snd_page_alloc         11432  1 snd_pcm
snd_opl3_lib           10336  1 snd_cmipci
snd_timer              24900  3 snd_seq,snd_pcm,snd_opl3_lib
snd_hwdep               9312  2 snd_sb16_csp,snd_opl3_lib
gameport                4608  1 snd_cmipci
snd_mpu401_uart         7776  1 snd_cmipci
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8040  4 snd_seq_oss,snd_seq,snd_opl3_lib,snd_rawmidi
snd                    55300  22 snd_seq_oss,snd_seq_midi_event,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_sb16_dsp,snd_sb16_csp,snd_sb_common,snd_cmipci,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10112  2 snd
piix                   13088  1
ehci_hcd               30756  0
joydev                  9728  0
usbhid                 31392  0
uhci_hcd               31952  0
usbcore               115684  5 ehci_hcd,usbhid,uhci_hcd
shpchp                 99340  0
pciehp                 96108  0
pci_hotplug            33680  2 shpchp,pciehp
parport_pc             34752  1
md                     48552  0
dm_mod                 57308  1
capability              4520  0
commoncap               7072  1 capability
lp                     10724  0
parport                40712  2 parport_pc,lp
evdev                   9440  0
ide_generic             1408  0
ide_disk               18752  0
ide_cd                 41572  0
ide_core              136120  4 piix,ide_generic,ide_disk,ide_cd
cdrom                  39392  1 ide_cd
mousedev               10220  1
psmouse                19720  0
ext3                  123880  1
jbd                    60824  1 ext3
mbcache                 9092  1 ext3
sd_mod                 21344  4
ata_piix                8004  5
libata                 40292  1 ata_piix
scsi_mod              122508  2 sd_mod,libata
unix                   28304  778
fan                     3980  0
thermal                12976  0
processor              17392  1 thermal
font                    8352  0
vesafb                  6560  0
cfbcopyarea             3712  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3616  1 vesafb

---

### Post by scoon on 2005-02-14
Hey there, 

If you have onboard sound and this is another card then try and disable on board audio.

scoon

---

### Post by jamaas on 2005-02-15
Thanks Scoon,

I managed to get it working but only from Real via the network, still can not get any sound fom CD drive!   Any suggestions how to remedy this?  I also can not  read a data disk when in this drive?

Thanks

Jim

[QUOTE=scoon]Hey there, 

If you have onboard sound and this is another card then try and disable on board audio.

scoon[/QUOTE]

---

### Post by scoon on 2005-02-15
Hey there, 

Are you certain that the drive is in working order ?

scoon

---

### Post by jamaas on 2005-02-16
Hi Scoon,

I know it all works when I boot to MS (spit!) Windows!  It is weird though.  I use a similar setup at home on a notebook and I can read/write to the cd very easily, in fact it puts an icon on the desktop for me.  With this computer I can even go as far as going to directory /media/cdrom or /media/cdrom0 and asking it ls and nothing happens ... 

When I put a music cd in the drive, and start gnome cd player, it starts and plays the songs and stuff but there is no sound out of anything.  

I wonder if the setting in the fstab is correct?  No new equipment has been added or removed since the original install but for some reason is installed as /dev/hdc.  

Do you know how to use diagnostics to (lspci and the like) to find if the settings are correct?

TIA

Jim


[QUOTE=scoon]Hey there, 

Are you certain that the drive is in working order ?

scoon[/QUOTE]

---

### Post by scoon on 2005-02-16
Hey there, 

The place to start would be with dmesg.  Do a man dmesg to learn more about it. Read over the output from dmesg to see where your cdrom drive is.  You can use dmesg | less to get one line at a time or try dmesg |  grep -i cd to filter out a lot of the other entries.  

scoon

---

### Post by jamaas on 2005-02-16
Thanks scoon,

I did the dmesg and saved it, cut a whole lot of stuff that I thought... was not relevant and posted the rest here.  It finds exactly the correct DVD/CD drive.  Strangely this doesn't show a sound card... shouldn't it ?
 
Next suggestion?

Thanks

Jim

=======================
00 - 00000000fed1a000 (reserved)
 BIOS-e820: 00000000fed1c000 - 00000000feda0000 (reserved)
127MB HIGHMEM available.
896MB LOWMEM available.
found SMP MP-table at 000ff780
On node 0 totalpages: 261935
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 225280 pages, LIFO batch:16
  HighMem zone: 32559 pages, LIFO batch:7
DMI 2.3 present.
ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f4eb0
ACPI: RSDT (v001 INTEL  D915GAG  0x20041201 MSFT 0x00000097) @ 0x3ff30000
ACPI: FADT (v002 INTEL  D915GAG  0x20041201 MSFT 0x00000097) @ 0x3ff30200
ACPI: MADT (v001 INTEL  D915GAG  0x20041201 MSFT 0x00000097) @ 0x3ff30390
ACPI: MCFG (v001 INTEL  D915GAG  0x20041201 MSFT 0x00000097) @ 0x3ff30400
ACPI: ASF! (v016 LEGEND I865PASF 0x00000001 INTL 0x02002026) @ 0x3ff36020
ACPI: TCPA (v001 INTEL  TBLOEMID 0x00000001 MSFT 0x00000097) @ 0x3ff360c0
ACPI: WDDT (v001 INTEL  OEMWDDT  0x00000001 INTL 0x02002026) @ 0x3ff360f4
ACPI: DSDT (v001 INTEL  D915GAG  0x00000001 INTL 0x02002026) @ 0x00000000

Built 1 zonelists
Kernel command line: root=/dev/sdb1 acpi=noirq ro quiet splash

Linux Plug and Play Support v0.97 (c) Adam Belay
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f2c40
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x325a, dseg 0xf0000
pnp: 00:0e: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:0e: ioport range 0xcf8-0xcff has been reserved
PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
PCI: Probing PCI hardware
PCI: Using IRQ router PIIX/ICH [8086/2640] at 0000:00:1f.0
PCI->APIC IRQ transform: (B0,I27,P0) -> 169
PCI->APIC IRQ transform: (B0,I29,P0) -> 209
PCI->APIC IRQ transform: (B0,I29,P1) -> 185
PCI->APIC IRQ transform: (B0,I29,P2) -> 177
PCI->APIC IRQ transform: (B0,I29,P3) -> 169
PCI->APIC IRQ transform: (B0,I29,P0) -> 209
PCI->APIC IRQ transform: (B0,I31,P0) -> 177
PCI->APIC IRQ transform: (B0,I31,P1) -> 185
PCI->APIC IRQ transform: (B0,I31,P1) -> 185
PCI->APIC IRQ transform: (B1,I0,P0) -> 169
PCI->APIC IRQ transform: (B6,I1,P0) -> 201
PCI->APIC IRQ transform: (B6,I8,P0) -> 193
highmem bounce pool size: 64 pages


devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0


Using anticipatory io scheduler
  Vendor: ATA       Model: Maxtor 6Y120M0    Rev: YAR5
  Type:   Direct-Access                      ANSI SCSI revision: 05
  Vendor: ATA       Model: Maxtor 6Y120M0    Rev: YAR5
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
SCSI device sdb: 240121728 512-byte hdwr sectors (122942 MB)
SCSI device sdb: drive cache: write back
 /dev/scsi/host1/bus0/target0/lun0: p1 p2 < p5 >
Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 497972k swap on /dev/sdb5.  Priority:-1 extents:1
EXT3 FS on sdb1, internal journal
mice: PS/2 mouse device common for all mice
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
hda: SONY DVD RW DW-D22A, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20


usbcore: registered new driver hiddev
input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1
input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ehci_hcd 0000:00:1d.7: Intel Corp. I/O Controller Hub USB2

Jim[QUOTE=scoon]Hey there, 

The place to start would be with dmesg.  Do a man dmesg to learn more about it. Read over the output from dmesg to see where your cdrom drive is.  You can use dmesg | less to get one line at a time or try dmesg |  grep -i cd to filter out a lot of the other entries.  

scoon[/QUOTE]

---

### Post by scoon on 2005-02-16
Hey there, 

dmesg would probably NOT show the sound card. lspci would be the tool to use for that.  Got to [http://www.alsa-project.org/](http://www.alsa-project.org/) here for some other advice on your card. 

scoon

---

