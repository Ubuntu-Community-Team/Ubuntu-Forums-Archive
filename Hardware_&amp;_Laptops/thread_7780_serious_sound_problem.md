---
title: "serious sound problem"
date: 2004-12-11
forum: Hardware &amp; Laptops
---

### Post by florin on 2004-12-11
Running gnoppix-0.8.2.2 on a Dell Latitude D600 laptop. There's no sound at all. When launching alsamixer manually, i get this error:
> # alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

The modules seem to be loaded fine:

> # lsmod
Module                  Size  Used by
md5                     3968  1
ipv6                  210848  6
lp                      9800  0
af_packet              15492  2
8250_pci               16384  0
ehci_hcd               26112  0
irtty_sir               5632  0
sir_dev                14140  1 irtty_sir
irda                  114936  1 sir_dev
8250_pnp                8320  0
pcspkr                  3532  0
evdev                   7680  0
tsdev                   5888  0
ds                     13952  4
yenta_socket           17280  1
pcmcia_core            55552  2 ds,yenta_socket
mini_fo                60768  2
usb_storage            61824  0
usbhid                 40000  0
ntfs                  109844  0
msdos                   7168  0
nls_iso8859_1           4224  1
snd_seq_oss            30080  0
snd_seq_midi_event      6272  1 snd_seq_oss
snd_seq                46096  4 snd_seq_oss,snd_seq_midi_event
snd_intel8x0           29292  0
gameport                3968  1 snd_intel8x0
snd_mpu401_uart         5888  1 snd_intel8x0
snd_rawmidi            18692  1 snd_mpu401_uart
snd_seq_device          6788  3 snd_seq_oss,snd_seq,snd_rawmidi
tg3                    75264  0
ipw2200                60748  0
firmware_class          7424  1 ipw2200
ieee80211              19684  1 ipw2200
ieee80211_crypt         4552  1 ieee80211
snd_intel8x0m          16008  0
snd_ac97_codec         59780  2 snd_intel8x0,snd_intel8x0m
snd_pcm_oss            47880  0
snd_mixer_oss          15872  1 snd_pcm_oss
snd_pcm                78208  3 snd_intel8x0,snd_intel8x0m,snd_pcm_oss
snd_timer              19456  2 snd_seq,snd_pcm
snd                    45188  13 snd_seq_oss,snd_seq_midi_event,snd_seq,snd_intel8x0,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0m,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               7392  1 snd
snd_page_alloc          9224  3 snd_intel8x0,snd_intel8x0m,snd_pcm
intel_agp              16664  1
agpgart                27596  1 intel_agp
parport_pc             33952  1
parport                33088  2 lp,parport_pc
8250                   28736  2 8250_pci,8250_pnp
serial_core            17408  1 8250
ohci1394               29056  0
ieee1394              300816  1 ohci1394
ohci_hcd               17792  0
uhci_hcd               27400  0
usbcore                93780  7 ehci_hcd,usb_storage,usbhid,ohci_hcd,uhci_hcd
thermal                11152  0
processor              16416  1 thermal
fan                     3468  0
button                  5400  0
battery                 8588  0
ac                      3980  0
ide_scsi               13316  0
rtc                     9544  0
cloop                  28928  2
a100u2w                10688  0
megaraid               36424  0
atp870u                22436  0
aha152x                34960  0
ide_cd                 36608  1


---

