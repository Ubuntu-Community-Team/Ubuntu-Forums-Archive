---
title: "Sound Blaster Live 24-Bit-Feisty"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by Linkerator on 2007-04-29
As with my large wave of questions, here is my new one. I have a Sound Blaster Live 24-Bit sound card. It worked perfectly for a bit. Now, Ubuntu is my OS, no more live CD's. I listened to some music, played some games. Now my sound doesn't work. Ubuntu detects both my sound devices, my Intel onboard Intel ICH5 and my PCI-slot Sound blaster (AD1980 for volume and CA106 for mic). It doesn't make a whisper. Are there any drivers or terminal commands to help?

---

### Post by simonn on 2007-04-29
[http://ubuntuforums.org/showpost.php?p=2459417&postcount=2](http://ubuntuforums.org/showpost.php?p=2459417&postcount=2)

---

### Post by Linkerator on 2007-04-29
I get ```
snd_usb_audio          79744  0 
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_ca0106             34592  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  2 snd_ca0106,snd_intel8x0
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_usb_lib,snd_ca0106,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                79876  5 snd_usb_audio,snd_ca0106,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23684  2 snd_seq,snd_pcm
ac97_bus                3200  1 snd_ac97_codec
snd                    54020  15 snd_usb_audio,snd_hwdep,snd_ca0106,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore               8672  1 snd
snd_page_alloc         10888  3 snd_ca0106,snd_intel8x0,snd_pcm
usbcore               134280  8 snd_usb_audio,snd_usb_lib,ov511,usb_storage,libusual,ehci_hcd,uhci_hcd

```

So the devices must be snd_ca0106, snd_intel8x0, and snd_ac97_c?

---

### Post by simonn on 2007-04-29
> **Linkerator said:**
> So the devices must be snd_ca0106, snd_intel8x0, and snd_ac97_c?

Nope, snd_ca0106 and snd_intel8x0. It also looks like you have som kind of USB sound - snd_usb_audio.

---

