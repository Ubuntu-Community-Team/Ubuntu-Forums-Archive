---
title: "No sound after switching to SLiM (instead of KDM)"
date: 2010-04-01
forum: Hardware
---

### Post by tau_neutrino on 2010-04-01
Greetings!

I've installed Karmic 64bit on my desktop. Previously I used ubuntus from version 5.04.

Everything was OK. But if I switch to SLiM instead of default KDM login manager, I have no sound. Maybe KDM runs some scripts/daemons on start that SLiM doesn't? Maybe you know what daemons should I run?

If I switch back to KDM everything works properly.'

Here are outputs of some informative commands:
```

neutrino@neutrino-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbff8000 irq 22
 1 [U0x46d0x8da    ]: USB-Audio - USB Device 0x46d:0x8da
                      USB Device 0x46d:0x8da at usb-0000:00:1a.2-2, full speed
neutrino@neutrino-desktop:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 2]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0- 0]: hardware dependent
  9: [ 0]   : control
 10: [ 1- 0]: digital audio capture
 11: [ 1]   : control
neutrino@neutrino-desktop:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio
neutrino@neutrino-desktop:~$ lsmod | grep snd
snd_usb_audio         102976  0
snd_usb_lib            19648  1 snd_usb_audio
snd_hda_codec_realtek   277860  1
snd_hda_intel          31880  0
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            44704  0
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0
snd_seq_oss            33440  0
snd_seq_midi            8192  0
snd_rawmidi            27296  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  13 snd_usb_audio,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm

```
lspci -v -v
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)                                                                       
        Subsystem: ASUSTeK Computer Inc. Device 829f                            
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-                                                   
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-                                                    
        Latency: 0, Cache Line Size: 32 bytes                                   
        Interrupt: pin A routed to IRQ 22                                       
        Region 0: Memory at fbff8000 (64-bit, non-prefetchable) [size=16K]      
        Capabilities: <access denied>                                           
        Kernel driver in use: HDA Intel                                         
        Kernel modules: snd-hda-intel   

```
Thank you in advance.

---

### Post by tau_neutrino on 2010-04-16
Hey! People! The issue is still actual!

Please HELP!

---

