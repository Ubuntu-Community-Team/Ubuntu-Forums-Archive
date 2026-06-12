---
title: "Large file copy on external USB hard disk is very slow"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by k.kid on 2007-09-11
Hello, I've got a Fujitsu-Siemens Lifebook C1020 with Ubuntu Feisty Fawn installed.
Problem starts when I copy a large file (about 4Gb) on my external USB hard disk. At the beginning I've an estimated time of 4/5 minute for the copy, but after about 20% of copy, the time was growing up till 130 hours and the copy got very very slow.
If I cancel the current copy and eject the disk, system write on disk for more than two minutes and then release it.
I tried different file-system format on disk (fat, ntfs, ext2, ext3) but nothing changed.
Of course, I know usb ports on my laptop are 1.1 and the connected disk is 2.0, but I think this configuration could not create a problem like that one.
Following more informations about the system configuration.

- Kernel version is 2.6.20-16-generic

- Configuration of PCI bus is:
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 70)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

- lsusb output is:
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000 

- lsmod output is:
Module                  Size  Used by
sg                         36252  0 
sd_mod                 23428  2 
usb_storage           72256  1 
libusual                 17936  1 usb_storage
usbhid                  26592  0 
hid                       27392  1 usbhid
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
vboxdrv                54664  0 
ppdev                         10116  0 
acpi_cpufreq                10056  0 
speedstep_lib               6148  0 
cpufreq_ondemand        9228  1 
cpufreq_conservative     8200  0 
cpufreq_stats               7360  0 
freq_table                   5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
ipv6                  268960  8 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
button                  8720  0 
ac                      6020  0 
dock                   10268  0 
container               5248  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
battery                10756  0 
video                  16388  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
savage                 34048  1 
drm                    81044  2 savage
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  3 
joydev                 10816  0 
snd_via82xx            29208  1 
gameport               16520  1 snd_via82xx
rt61                          245128  1 
snd_mpu401_uart         9472  1 snd_via82xx
pcmcia                     39212  0 
i2c_prosavage           5248  0 
i2c_algo_bit            8712  1 i2c_prosavage
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
i2c_viapro                  10132  0 
snd_via82xx_modem      16008  0 
snd_ac97_codec         98464  2 snd_via82xx,snd_via82xx_modem
parport_pc                36388  1 
parport                      36936  3 ppdev,lp,parport_pc
snd_seq_midi            9600  0 
snd_rawmidi               25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
i2c_core                    22656  4 i2c_ec,i2c_prosavage,i2c_algo_bit,i2c_viapro
ac97_bus                  3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                79876  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              23684  2 snd_seq,snd_pcm
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
via_ircc               27540  0 
pcspkr                  4224  0 
serio_raw               7940  0 
psmouse                38920  0 
snd                    54020  14 snd_via82xx,snd_mpu401_uart,snd_seq_oss,snd_via82xx_modem,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_timer,snd_seq_device
snd_page_alloc         10888  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore               8672  1 snd
irda                  201276  1 via_ircc
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
crc_ccitt               3072  1 irda
via_agp                11264  1 
agpgart                35400  2 drm,via_agp
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
af_packet              23816  6 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  5 sg,sd_mod,usb_storage,sbp2,libata
via82cxxx              10372  0 [permanent]
floppy                 59524  0 
generic                 5124  0 [permanent]
uhci_hcd               25360  0 
usbcore               134280  5 usb_storage,libusual,usbhid,uhci_hcd
8139cp                 25088  0 
8139too                27648  0 
mii                     6528  2 8139cp,8139too
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
capability              5896  0 
commoncap               8192  1 capability
vesafb                  9220  1 
fbcon                  42656  72 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit

----
Can anyone help me?
Thanks.

---

