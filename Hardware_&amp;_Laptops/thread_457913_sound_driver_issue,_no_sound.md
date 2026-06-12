---
title: "sound driver issue, no sound"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by skamatron3000 on 2007-05-29
gday skamatron here

Im haing troubles with my soundcard. I cant get any sound. Im currently using ubuntu 7.04. Tried various operating systems including slax blag and xp
```
Module                  Size  Used by
ipv6                  229504  10
snd_seq_dummy           2948  0
snd_seq_oss            30080  0
snd_seq_midi_event      5888  1 snd_seq_oss
snd_seq                44496  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_seq_device          6540  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd_pcm_oss            38432  1
snd_mixer_oss          15744  2 snd_pcm_oss
ohci_hcd               18436  0
intel_agp              19612  1
uhci_hcd               28688  0
ehci_hcd               29064  0
shpchp                 39616  0
i8xx_tco                5908  0
i2c_i801                7820  0
i2c_core               16784  1 i2c_i801
snd_intel8x0           28572  2
snd_ac97_codec         86688  1 snd_intel8x0
snd_ac97_bus            1920  1 snd_ac97_codec
snd_pcm                73864  3 snd_pcm_oss,snd_intel8x0,snd_ac97_codec
snd_timer              19332  2 snd_seq,snd_pcm
snd                    44132  10 snd_seq_dummy,snd_seq_oss,snd_seq,snd_seq_devi_oss,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               7136  3 snd
snd_page_alloc          7688  2 snd_intel8x0,snd_pcm
8139too                21760  0
mii                     4864  1 8139too
pcmcia                 30500  0
yenta_socket           23436  0
rsrc_nonstatic         11008  1 yenta_socket
pcmcia_core            34576  3 pcmcia,yenta_socket,rsrc_nonstatic
fuse                   33292  0
agpgart                28080  1 intel_agp
psmouse                34952  0
nls_iso8859_2           4480  0
nls_iso8859_1           3968  0
nls_cp437               5632  0
unionfs                63136  1
squashfs               40628  10
```
```

00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4           rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4           rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4           rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controll
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/D            Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4
02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-813
```

Thankx alot ur fellow ubuntur

---

### Post by voltagex on 2007-05-29
Didn't I say don't use SMS speak? ;)

Hi, I'm helping skarmatron with Ubuntu as I'm about 10km away from him.

We think this sound chip is a normal AC97 thing, but it's not loading ALSA, only OSS drivers.
It's on an intel based board, Gigabyte I think. Skarmatron, can you grab the model number of the motherboard?

---

### Post by skamatron3000 on 2007-05-29
gigabyte 8ie533 with an intergrated realtek alc650 sound card

---

### Post by skamatron3000 on 2007-05-29
we have just located a manual for the motherboard to investigate the jumper settings [http://www.gigabyte.com.tw/Support/Motherboard/Manual_DownloadFile.aspx?FileType=Manual&FileID=15278](http://www.gigabyte.com.tw/Support/Motherboard/Manual_DownloadFile.aspx?FileType=Manual&FileID=15278)

---

### Post by voltagex on 2007-05-29
Jumper settings should not affect the sound. Also, you may have to wait til the morning as there are a lot of people in different time zones here!

---

