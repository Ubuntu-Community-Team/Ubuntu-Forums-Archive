---
title: "The audio is not working in debian installation"
date: 2009-08-14
forum: Hardware
---

### Post by m_alnaanah on 2009-08-14
I have installed debian, with lxde interface but the audio is not working and the /dev/audio file is not there.

the output of lspci is:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:07.0 Communication controller: Agere Systems 56k WinModem (rev 01)
00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)
06:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)


and the output of lsmod command is:

Module                  Size  Used by
aes_i586                7744  0 
aes_generic            29256  1 aes_i586
savage                 26464  2 
drm                    65192  3 savage
rfcomm                 28272  0 
l2cap                  17248  5 rfcomm
bluetooth              44868  4 rfcomm,l2cap
ppdev                   6500  0 
lp                      8164  0 
ipv6                  235364  14 
speedstep_lib           4516  0 
cpufreq_conservative     5960  0 
cpufreq_userspace       3172  0 
cpufreq_stats           3776  0 
cpufreq_powersave       1856  0 
cpufreq_ondemand        6476  0 
freq_table              4224  2 cpufreq_stats,cpufreq_ondemand
nls_utf8                1760  1 
nls_cp437               5568  1 
vfat                    9184  1 
fat                    40896  1 vfat
nls_base                6820  4 nls_utf8,nls_cp437,vfat,fat
reiserfs              189888  2 
fuse                   42908  1 
loop                   12748  0 
snd_ymfpci             28224  0 
gameport               10700  1 snd_ymfpci
arc4                    1824  2 
snd_ac97_codec         88484  1 snd_ymfpci
ac97_bus                1728  1 snd_ac97_codec
snd_pcm_oss            32832  0 
snd_mixer_oss          12320  1 snd_pcm_oss
ecb                     2624  2 
crypto_blkcipher       15236  1 ecb
snd_pcm                62596  3 snd_ymfpci,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib            9344  1 snd_ymfpci
snd_hwdep               6212  1 snd_opl3_lib
snd_page_alloc          7816  2 snd_ymfpci,snd_pcm
snd_mpu401_uart         6368  1 snd_ymfpci
snd_seq_dummy           2660  0 
ath5k                  87264  0 
mac80211              139712  1 ath5k
cfg80211               21576  2 ath5k,mac80211
pcmcia                 29548  0 
firmware_class          6816  2 snd_ymfpci,pcmcia
parport_pc             22500  1 
parport                30988  3 ppdev,lp,parport_pc
snd_seq_oss            24992  0 
toshiba_acpi            5336  0 
video                  16432  0 
output                  2912  1 video
snd_seq_midi            5728  0 
snd_rawmidi            18528  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6432  2 snd_seq_oss,snd_seq_midi
snd_seq                41456  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
container               3456  0 
battery                10180  0 
ac                      4196  0 
snd_timer              17800  4 snd_ymfpci,snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          6380  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  6096  0 
snd                    45604  13 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6368  1 snd
serio_raw               4740  0 
donauboe                9376  0 
i2c_piix4               7216  0 
pcspkr                  2432  0 
yenta_socket           20620  3 
rsrc_nonstatic          9504  1 yenta_socket
pcmcia_core            31892  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                32336  0 
intel_agp              22556  1 
shpchp                 25528  0 
i2c_core               19828  1 i2c_piix4
irda                   95512  1 donauboe
pci_hotplug            23460  1 shpchp
crc_ccitt               2080  2 donauboe,irda
agpgart                28776  2 drm,intel_agp
evdev                   8000  4 
sd_mod                 22200  0 
ext3                  105512  1 
jbd                    39444  1 ext3
mbcache                 7108  1 ext3
ide_cd_mod             27652  0 
cdrom                  30176  1 ide_cd_mod
ide_disk               10496  6 
ide_pci_generic         3908  0 [permanent]
usb_storage            77024  0 
piix                    6568  0 [permanent]
ide_core               96136  4 ide_cd_mod,ide_disk,ide_pci_generic,piix
floppy                 47748  0 
ata_generic             4676  0 
uhci_hcd               18672  0 
libata                140416  1 ata_generic
scsi_mod              129324  3 sd_mod,usb_storage,libata
usbcore               118224  3 usb_storage,uhci_hcd
dock                    8304  1 libata
thermal                15228  0 
processor              32544  2 thermal
fan                     4164  0 
thermal_sys            10856  4 video,thermal,processor,fan



any help please

---

