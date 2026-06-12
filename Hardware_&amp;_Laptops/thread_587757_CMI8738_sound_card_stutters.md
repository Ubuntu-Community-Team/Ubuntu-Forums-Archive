---
title: "CMI8738 sound card stutters"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by davidsrsb on 2007-10-23
Ubuntu 7.10, CMI8738 card in a Dell E520 core2duo
The sound stutters when I move the mouse around and audio file play stalls after a while
The PC has onboard Intel + Stac sound that is disable in the bios as it did not work under Feisty.

relevant extracts of diagnostics:
lspci
03:02.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

lsmod
snd_cmipci             37024  1 
gameport               16776  1 snd_cmipci
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
snd_opl3_lib           11520  1 snd_cmipci
snd_hwdep              10244  1 snd_opl3_lib
snd_mpu401_uart         9600  1 snd_cmipci
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9228  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  18 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

---

