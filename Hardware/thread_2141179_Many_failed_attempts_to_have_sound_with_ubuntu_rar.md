---
title: "Many failed attempts to have sound with ubuntu raring on macbook air 1,1"
date: 2013-05-01
forum: Hardware
---

### Post by twinturbotom on 2013-05-01
I have no sound...never had with any ubuntu release on this machine :( and I've tried many potential slutions.  ArchLinux and ALSA wiki sites have been my main resource as well as this forum.  
I'm missing something, before mac OSX was removed speakers worked and I do hear a sound during boot up (during a long white splash screen I still need to fix!) so I don't believe my hardware is bad.

I've tried so many things I'm not sure if I've caused more porblmes or not.  Below are some of the commands and outputs I'm using to diagnose.  Any direction or thoughts would be helpful....


Thank you!

modified /etc/modprobe.d/alsa-base.conf with one of these entries:
```
options snd_hda_intel index=0
options snd_hda_intel model=intel-mac-auto
```

```
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x90500000 irq 43
```

```
$ cat /proc/asound/devices
  1:        : sequencer
  2: [ 0- 0]: digital audio playback
  3: [ 0- 0]: digital audio capture
  4: [ 0- 0]: hardware dependent
  5: [ 0]   : control
 33:        : timer
```

```
$ cat /proc/asound/pcm
00-00: ALC889A Analog : ALC889A Analog : playback 1 : capture 1

```
```

$ cat /proc/asound/modules
 0 snd_hda_intel
```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$ lsmod | grep snd
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  3 
snd_hda_codec         136453  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd

```

```
$ amixer -d
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [0.20dB]
  Front Right: Playback 254 [100%] [0.20dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 12 [39%] [-16.50dB] [off]
  Front Right: Playback 12 [39%] [-16.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 37 [80%] [21.00dB] [on]
  Front Right: Capture 37 [80%] [21.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'

```

Cut the speaker test short as no sound is heard
```
$ speaker-test
speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 11.380310
 0 - Front Left
Time per period = 11.379785
```

```
modprobe -c | grep snd_intel

blacklist snd_intel8x0m
options snd_intel8x0m index=-2
alias pci:v00001022d00007445sv*sd*bc*sc*i* snd_intel8x0
alias pci:v00001022d00007446sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v00001022d0000746Dsv*sd*bc*sc*i* snd_intel8x0
alias pci:v00001022d0000746Esv*sd*bc*sc*i* snd_intel8x0m
alias pci:v00001039d00007012sv*sd*bc*sc*i* snd_intel8x0
alias pci:v00001039d00007013sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v000010B9d00005455sv*sd*bc*sc*i* snd_intel8x0
alias pci:v000010DEd0000003Asv*sd*bc*sc*i* snd_intel8x0
alias pci:v000010DEd00000059sv*sd*bc*sc*i* snd_intel8x0
alias pci:v000010DEd00000069sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v000010DEd0000006Asv*sd*bc*sc*i* snd_intel8x0
alias pci:v000010DEd00000089sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v000010DEd0000008Asv*sd*bc*sc*i* snd_intel8x0
alias pci:v000010DEd000000D9sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v000010DEd000000DAsv*sd*bc*sc*i* snd_intel8x0
alias pci:v000010DEd000000EAsv*sd*bc*sc*i* snd_intel8x0
alias pci:v000010DEd000001B1sv*sd*bc*sc*i* snd_intel8x0
alias pci:v000010DEd000001C1sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v000010DEd0000026Bsv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d00002415sv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d00002416sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v00008086d00002425sv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d00002426sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v00008086d00002445sv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d00002446sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v00008086d00002485sv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d00002486sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v00008086d000024C5sv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d000024C6sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v00008086d000024D5sv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d000024D6sv*sd*bc*sc*i* snd_intel8x0m
alias pci:v00008086d000025A6sv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d0000266Dsv*sd*bc*sc*i* snd_intel8x0m
alias pci:v00008086d0000266Esv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d00002698sv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d000027DDsv*sd*bc*sc*i* snd_intel8x0m
alias pci:v00008086d000027DEsv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d00007195sv*sd*bc*sc*i* snd_intel8x0
alias pci:v00008086d00007196sv*sd*bc*sc*i* snd_intel8x0m
```

---

