---
title: "USB Problem"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by Sebby123 on 2008-02-03
Hey, I'm new to Ubuntu so treat me like I'm a small child.

Heres the problem. When I insert my USB pen drive the USB ports at the back of my computer die. First my mouse stops working, then the power goes. Unplugging it and replugging it doesn't work. I have to shut it down for it to work again.

I plug the USB pen into the front USB's.

Heres my lspci

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

lsmod

```

Module                  Size  Used by
joydev                 11328  0 
snd_usb_audio          81024  0 
snd_usb_lib            17920  1 snd_usb_audio
xpad                    9988  0 
snd_hwdep              10244  1 snd_usb_audio
usb_storage            73024  0 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
ipv6                  273892  8 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
dock                   10656  0 
container               5504  0 
ac                      6148  0 
video                  18060  0 
button                  8976  0 
sbs                    19592  0 
battery                11012  0 
lp                     12580  0 
snd_intel8x0           34972  4 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  5 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
sn9c102               120708  0 
snd_seq_oss            33152  0 
compat_ioctl32          2304  1 sn9c102
gspca                 608336  0 
snd_seq_midi            9600  0 
videodev               29312  2 sn9c102,gspca
v4l2_common            18432  2 sn9c102,videodev
v4l1_compat            15364  1 videodev
usbhid                 29536  0 
snd_rawmidi            25728  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hid                    28928  1 usbhid
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
analog                 13344  0 
gameport               16776  1 analog
snd                    54660  18 snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
nvidia               6221648  34 
pcspkr                  4224  0 
i2c_sis96x              6404  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
sis_agp                10116  1 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  2 nvidia,sis_agp
i2c_core               26112  2 nvidia,i2c_sis96x
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
floppy                 60004  0 
sis900                 24960  0 
mii                     6528  1 sis900
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  11 snd_usb_audio,snd_usb_lib,xpad,usb_storage,libusual,sn9c102,gspca,usbhid,ehci_hcd,ohci_hcd
pata_sis               15236  2 
ata_generic             8452  0 
libata                125168  2 pata_sis,ata_generic
scsi_mod              147084  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

lsusb (before pen drive)

```

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0c45:600d Microdia 
Bus 001 Device 001: ID 0000:0000 

```

lsusb (pen drive in)

```

Bus 003 Device 007: ID 1976:6025  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0c45:600d Microdia 
Bus 001 Device 001: ID 0000:0000 

```

I hope all of that is usefull.

Thanks in advance.

---

