---
title: "Tp 600e no sound ubuntu 8.10&gt;9.04"
date: 2009-05-24
forum: Hardware
---

### Post by kim67 on 2009-05-24
My old tp not found soundcard cs 4610/11...only if i enabled quickboot in to the bios and add acpi= force into kernel boot list then sound works... But then machine dont found wireless 3g card huawei e169  in to usb.... and pcmia plases is lost too.... can somebody help me....

-l; lsmod |grep snd

aplay: device_list:217: äänikortteja ei löytynyt...(no souncards found) my own tag
snd_cs46xx             88296  0 
gameport               19340  1 snd_cs46xx
snd_ac97_codec        112292  1 snd_cs46xx
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  10 snd_cs46xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_cs46xx,snd_pcm

"lspci"
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1251A
00:02.1 CardBus bridge: Texas Instruments PCI1251A
00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
06:00.0 USB Controller: NEC Corporation USB (rev 43)
06:00.1 USB Controller: NEC Corporation USB (rev 43)
06:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

