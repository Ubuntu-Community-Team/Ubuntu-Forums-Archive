---
title: "TV Card Tuner Problem (Composite Working)"
date: 2008-08-01
forum: General Help
---

### Post by kempy1000 on 2008-08-01
Hello,
Im trying to get my Kworld PVR-7134 Tv card working.
I have searched and searched and tried everything i can find on the forums and google but the most i have managed to get is a working composite input in tvtime.
I am trying to be able to view tv on it. 
{Eventually for mythtv to use}
tvtime always says no signal detected.

I have posted the outputs from forum found commands:

dmesg |grep saa
```

[   25.956148] saa7130/34: v4l2 driver version 0.2.14 loaded
[   25.956282] saa7134[0]: found at 0000:00:0a.0, rev: 1, irq: 18, latency: 32, mmio: 0xdffffc00
[   25.956291] saa7134[0]: subsystem: 1131:0000, board: FlyTV mini Asus Digimatrix [card=64,insmod option]
[   25.956316] saa7134[0]: board init: gpio is 407f
[   26.066610] saa7134[0]: Huh, no eeprom present (err=-5)?
[   26.545551] tuner 1-0060: chip found @ 0xc0 (saa7134[0])
[   27.215130] saa7134[0]: registered device video0 [v4l2]
[   27.215167] saa7134[0]: registered device vbi0
[   27.215202] saa7134[0]: registered device radio0
[   27.487420] saa7134 ALSA driver for DMA sound loaded
[   27.487479] saa7134[0]/alsa: saa7134[0] at 0xdffffc00 irq 18 registered as card -2
[  345.416906] saa7134 ALSA driver for DMA sound unloaded
[  409.413592] saa7130/34: v4l2 driver version 0.2.14 loaded
[  409.413695] saa7134[0]: found at 0000:00:0a.0, rev: 1, irq: 18, latency: 32, mmio: 0xdffffc00
[  409.413705] saa7134[0]: subsystem: 1131:0000, board: Kworld/Tevion V-Stream Xpert TV PVR7134 [card=59,insmod option]
[  409.413726] saa7134[0]: board init: gpio is 407f
[  409.413841] input: saa7134 IR (Kworld/Tevion V-Str as /devices/pci0000:00/0000:00:0a.0/input/input6
[  409.618068] tuner 1-0060: chip found @ 0xc0 (saa7134[0])
[  410.199622] saa7134[0]: Huh, no eeprom present (err=-5)?
[  410.406812] saa7134 IR (Kworld/Tevion V-Str: unknown key: key=0x03 raw=0x03 down=1
[  413.240862] saa7134[0]: registered device video0 [v4l2]
[  413.240899] saa7134[0]: registered device vbi0
[  413.240928] saa7134[0]: registered device radio0
[  413.419387] saa7134 ALSA driver for DMA sound loaded
[  413.419450] saa7134[0]/alsa: saa7134[0] at 0xdffffc00 irq 18 registered as card -2

```

lsmod
```

saa7134_alsa           15424  0
saa7134               132048  1 saa7134_alsa
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
w83627hf               23316  0
hwmon_vid               4352  1 w83627hf
parport_pc             36644  0
lp                     12324  0
parport                37704  2 parport_pc,lp
loop                   19076  0
snd_via82xx            29848  2
gameport               16008  1 snd_via82xx
ipv6                  272804  196
snd_ac97_codec        101028  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_mpu401_uart         9984  1 snd_via82xx
snd_seq_dummy           4996  0
snd_pcm_oss            42272  0
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                78852  5 saa7134_alsa,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            35456  0
snd_seq_midi            9504  0
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
tuner                  42912  0
tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
via_ircc               27924  0
compat_ioctl32          2304  1 saa7134
videobuf_dma_sg        15108  2 saa7134_alsa,saa7134
videobuf_core          18820  2 saa7134,videobuf_dma_sg
ir_kbd_i2c             10768  1 saa7134
irda                  203068  1 via_ircc
snd                    56996  14 saa7134_alsa,snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_seq_dummy,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0
ir_common              36100  2 saa7134,ir_kbd_i2c
snd_page_alloc         11784  2 snd_via82xx,snd_pcm
crc_ccitt               3072  1 irda
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
videodev               29312  1 saa7134
v4l2_common            18304  3 saa7134,tuner,videodev
v4l1_compat            15492  2 saa7134,videodev
soundcore               8800  2 snd
via_agp                11136  1
i2c_viapro              9876  0
evdev                  12928  0
agpgart                34760  1 via_agp
i2c_core               24832  9 saa7134,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,ir_kbd_i2c,i2c_viapro
pcspkr                  4224  0
ext3                  136584  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36496  0
sr_mod                 17828  0
cdrom                  37280  1 sr_mod
sd_mod                 30720  3
pata_acpi               8320  0
pata_via               13316  2
ata_generic             8324  0
via_rhine              26888  0
mii                     6400  1 via_rhine
libata                159344  3 pata_acpi,pata_via,ata_generic
ehci_hcd               38412  0
uhci_hcd               27152  0
scsi_mod              151180  4 sg,sr_mod,sd_mod,libata
usbcore               146028  3 ehci_hcd,uhci_hcd
thermal                16796  0
processor              37000  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1

```

/etc/modprobe.d/options
```

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
options saa7134 card=59 tuner=54

```

Thanks
Chris

---

