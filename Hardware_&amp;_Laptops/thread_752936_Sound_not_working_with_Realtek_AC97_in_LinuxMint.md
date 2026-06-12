---
title: "Sound not working with Realtek AC97 in LinuxMint"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by 1002285 on 2008-04-12
I cannot get sound to work on my desktop. I bought it as used, but I still try to believe the seller didn't lie about it working.
I found other threads here, but so far I don't seem to find an answer from here.
My lspci and lsmod commands give thes answers, and ac97 are included in them both, I think.

so:
lspci:
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

and lsmod:
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
sg                     36764  0 
sd_mod                 30336  2 
usb_storage            73024  1 
libusual               18448  1 usb_storage
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
video                  18060  0 
button                  8976  0 
ac                      6148  0 
sbs                    19592  0 
dock                   10656  0 
container               5504  0 
battery                11012  0 
lp                     12580  0 
snd_via82xx            29336  2 
gameport               16776  1 snd_via82xx
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
via_ircc               27668  0 
irda                  202300  1 via_ircc
serio_raw               8068  0 
psmouse                39952  0 
crc_ccitt               3072  1 irda
snd                    54660  14 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro             10004  0 
shpchp                 34580  0 
soundcore               8800  1 snd
pci_hotplug            32704  1 shpchp
via_agp                11264  1 
agpgart                35016  1 via_agp
i2c_core               26112  1 i2c_viapro
evdev                  11136  4 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ide_disk               18560  5 
usbhid                 29536  0 
hid                    28928  1 usbhid
via82cxxx              10372  0 [permanent]
ide_core              116804  4 usb_storage,ide_cd,ide_disk,via82cxxx
floppy                 60004  0 
via_rhine              25992  0 
mii                     6528  1 via_rhine
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  4 sg,sd_mod,usb_storage,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
r8169                  32260  0 
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
capability              5896  0 
commoncap               8320  1 capability
fuse                   47124  5

---

