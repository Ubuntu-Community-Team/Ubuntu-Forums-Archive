---
title: "No sound on Asus A6000"
date: 2008-05-23
forum: Hardware
---

### Post by Ilya Evseev on 2008-05-23
There is an Asus A6000 notebook,
initially with Ubuntu 7.10, now with 8.04.
All hardware works properly, except sound.

Sound card is detected correctly.
Multimedia keys are handled with notifications on the screen.
But speakers are dead (under Windoze all works fine).

System-Parameters-Sound contains following values for Mixer:
- Intel 80801DB-ICH4 (default)
- Realtek ALC650F (OSS Mixer)

Any ideas? :confused:

lspci:
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
```

lsmod:
```
Module                  Size  Used by
isofs                  36388  1 
udf                    88612  0 
ipv6                  267780  8 
i915                   32512  2 
drm                    82580  3 i915
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
lp                     12324  0 
loop                   18948  0 
joydev                 13120  0 
pcmcia                 40876  0 
psmouse                40336  0 
serio_raw               7940  0 
arc4                    2944  2 
irtty_sir               9728  0 
ecb                     4480  2 
blkcipher               8324  1 ecb
sir_dev                17412  1 irtty_sir
evdev                  13056  7 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_intel8x0           35356  3 
irda                  203068  2 irtty_sir,sir_dev
rt2500pci              20352  0 
rt2x00pci              11264  1 rt2500pci
rt2x00lib              22528  2 rt2500pci,rt2x00pci
snd_ac97_codec        101028  1 snd_intel8x0
crc_ccitt               3072  1 irda
rfkill                  8592  2 rt2x00lib
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  3 rt2500pci,rt2x00pci,rt2x00lib
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcspkr                  4224  0 
cfg80211               15112  1 mac80211
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
eeprom_93cx6            3200  1 rt2500pci
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
video                  19856  0 
battery                14212  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
output                  4736  1 video
ac                      6916  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
asus_laptop            19064  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
led_class               6020  1 asus_laptop
button                  9232  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
ata_piix               19588  3 
8139too                27520  0 
ohci1394               33584  0 
pata_acpi               8320  0 
ieee1394               93752  2 sbp2,ohci1394
8139cp                 24704  0 
mii                     6400  2 8139too,8139cp
libata                159344  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 

```

---

### Post by numbercruncher86 on 2008-10-01
go to system - preferences - sound and check their if ALSA is selected because with my asus notebook it did not work with Realtek!

---

