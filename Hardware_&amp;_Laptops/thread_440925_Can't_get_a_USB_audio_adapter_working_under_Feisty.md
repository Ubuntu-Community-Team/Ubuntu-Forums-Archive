---
title: "Can't get a USB audio adapter working under Feisty"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by jehosephat on 2007-05-12
I've just upgraded to Feisty on my Compaq Evo n1000c, which lost sound several months ago (due to the on-board sound simply dying ... she's an old beast).  I bought a cheap 5.1 audio adapter (USB) and had it working under Edgy (just by playing with the sound preference settings, as I recall), but it's not working now.

None of the settings under **Sound > Preferences** (Autodetect, USB-audio, Intel..., ESD, ALSA, OSS) gives me any sound.

<lsmod|grep snd> gives me:

> snd_usb_audio          78592  0 
snd_usb_lib            16256  1 snd_usb_audio
snd_hwdep               9092  1 snd_usb_audio
snd_intel8x0           32796  1 
snd_ac97_codec         97184  1 snd_intel8x0
ac97_bus                2304  1 snd_ac97_codec
snd_pcm_oss            43264  0 
snd_pcm                76680  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          16512  1 snd_pcm_oss
snd_seq_dummy           3844  0 
snd_seq_oss            31616  0 
snd_seq_midi            8576  0 
snd_rawmidi            24448  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7424  2 snd_seq_oss,snd_seq_midi
snd_seq                49648  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    51716  14 snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc          9992  2 snd_intel8x0,snd_pcm
usbcore               131480  8 ndiswrapper,snd_usb_audio,xpad,usbhid,snd_usb_lib,ehci_hcd,ohci_hcd


Any suggestions about what I can do to diagnose this?

---

### Post by heimo on 2007-05-12
Check you audio levels with alsamixer:
```
alsamixer -c1
```
Or with -c0. Use arrow keys, space, m-key (mute), and tabulator to navigate.

---

### Post by jehosephat on 2007-05-13
Under alsamixer, all levels are at 100, PCMcapt is "Input 1" (maybe because card 0 is the dead onboard audio, and card 1 is the USB audio adapter? ), and Auto Gain Control is Off.

Output from <aplay -l>:
> **** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Here's another clue ...
following another thread's advice, I tried <sudo dpkg-reconfigure alsa-source>, and before the new window opened, got this:
> X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

... four times.  After building snd-usb-audio with and without ISA PnP support and Debugging Code, I ran 
<sudo module-assistant a-i alsa-source> ... which exited after failing to build the driver successfully.

Any idea what device 171 refers to, or how I could find out?  Should I be disabling the dead on-board card somehow?  I googled the X error, but found nothing with the same major opcode.

---

### Post by heimo on 2007-05-13
> **jehosephat said:**
> Should I be disabling the dead on-board card somehow?

Yeah, that's worth trying. Find if there's option in BIOS - if not, there may be jumper on motherboard to disable integrated audio. It's also possible that these do not exist.

---

