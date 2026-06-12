---
title: "sound problems"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by asaone on 2007-06-14
I have a Toshiba satellite a100 and for the life of me have not been able to get the sound working.  Here is the outputts.  The sound card is an intel HD using a CONEXANT chipset

lsmod | grep snd
snd_hda_intel         244632  2
snd_pcm_oss            44672  1
snd_pcm                81028  2 snd_hda_intel,snd_pcm_osshi
snd_mixer_oss          17792  1 snd_pcm_oss
snd_seq_oss            35200  0
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54000  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
snd                    56324  10 snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  2 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
 List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

All help is much appresiated, thank you.  

Ken

---

### Post by Scooter7 on 2007-06-22
I'm having a similar problem, only with a Toshiba P100 - outputs:

> snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

I've tried some stuff listed on [www.ubuntuguide.org](www.ubuntuguide.org), but I don't know the model for my card, so I can't use the suggestion on there.

As Ken said, any help would indeed be appreciated.

Thanks,

---

### Post by Scooter7 on 2007-06-22
*bump*

---

### Post by rax_m on 2007-06-22
On my Toshiba P100-429 I had to manually update the ACPI and install the latest Alsa drivers

[http://ubuntuforums.org/showthread.php?t=412986&highlight=p100-429](http://ubuntuforums.org/showthread.php?t=412986&highlight=p100-429)

Not sure if yours is the same problem.. but you could possibly start by upgrading Alsa to see if that works then try the ACPI patches.

---

