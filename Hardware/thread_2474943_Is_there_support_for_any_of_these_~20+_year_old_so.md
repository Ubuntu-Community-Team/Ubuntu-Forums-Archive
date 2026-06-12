---
title: "Is there support for any of these ~20+ year old sound cards in 2022"
date: 2022-05-12
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2022-05-12
I have 3 old pci sound cards
[LIST]
[*]SB0200
[*]SB0350 + external I/O hub
[*]SB0460
[/LIST]
hoping to be able to use one of these for multiple outputs in addition to my onboard audio

maybe i can use the game pad/joystick port for buttons to run scripts? (volume, pause, play, output select,etc. w/ mpd)

my only exp with old sound cards and Linux was with some cheap crap that was in a old HP prebuilt, i think i was attached to the 56k modem or something strange like that

---

### Post by rsteinmetz70112 on 2022-05-13
I'd just try them and see if they are recognized.

---

### Post by Yellow Pasque on 2022-05-13
The SB0350  (don't know if external hub will work though):
[https://github.com/torvalds/linux/blob/f3f19f939c11925dadd3f4776f99f8c278a7017b/sound/pci/emu10k1/emu10k1_main.c#L1498](https://github.com/torvalds/linux/blob/f3f19f939c11925dadd3f4776f99f8c278a7017b/sound/pci/emu10k1/emu10k1_main.c#L1498)

A report that SB0460 works:
[https://forums.linuxmint.com/viewtopic.php?t=311120](https://forums.linuxmint.com/viewtopic.php?t=311120)

---

### Post by pqwoerituytrueiwoq on 2022-05-14
My PCIe to PCI adapter just came in yesterday, just got my server rebuilt today, tried to check it out on a live usb, but i had issues with the hdmi cable being a POS and dropping signal, but it was good enough to config the bios, the card shows up in aplay and lspci and has a driver assigned, i think it might JUST WORK [-o<

```
[FONT=monospace][COLOR=#000000]1d:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 04) [/COLOR]
1e:00.0 Multimedia audio controller [0401]: Creative Labs EMU10k2/CA0100/CA0102/CA10200 [Sound Blaster Audigy Series] [1102:0004] (rev 04) 
        Subsystem: Creative Labs SB0350 Audigy 2 ZS [1102:2002] 
        Kernel driver in use: snd_emu10k1 
        Kernel modules: snd_emu10k1 
1e:00.1 Input device controller [0980]: Creative Labs SB Audigy Game Port [1102:7003] (rev 04) 
        Subsystem: Creative Labs SB Audigy Game Port [1102:0040] 
        Kernel driver in use: Emu10k1_gameport 
        Kernel modules: emu10k1_gp 
1e:00.2 FireWire (IEEE 1394) [0c00]: Creative Labs SB Audigy FireWire Port [1102:4001] (rev 04) 
        Subsystem: Creative Labs SB Audigy FireWire Port [1102:0010] 
        Kernel driver in use: firewire_ohci 
        Kernel modules: firewire_ohci
[/FONT]
```
```
[FONT=monospace][COLOR=#000000]**** List of PLAYBACK Hardware Devices **** [/COLOR]
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback] 
  Subdevices: 32/32 
  Subdevice #0: subdevice #0 
  Subdevice #1: subdevice #1 
  Subdevice #2: subdevice #2 
  Subdevice #3: subdevice #3 
  Subdevice #4: subdevice #4 
  Subdevice #5: subdevice #5 
  Subdevice #6: subdevice #6 
  Subdevice #7: subdevice #7 
  Subdevice #8: subdevice #8 
  Subdevice #9: subdevice #9 
  Subdevice #10: subdevice #10 
  Subdevice #11: subdevice #11 
  Subdevice #12: subdevice #12 
  Subdevice #13: subdevice #13 
  Subdevice #14: subdevice #14 
  Subdevice #15: subdevice #15 
  Subdevice #16: subdevice #16 
  Subdevice #17: subdevice #17 
  Subdevice #18: subdevice #18 
  Subdevice #19: subdevice #19 
  Subdevice #20: subdevice #20 
  Subdevice #21: subdevice #21 
  Subdevice #22: subdevice #22 
  Subdevice #23: subdevice #23 
  Subdevice #24: subdevice #24 
  Subdevice #25: subdevice #25 
  Subdevice #26: subdevice #26 
  Subdevice #27: subdevice #27 
  Subdevice #28: subdevice #28 
  Subdevice #29: subdevice #29 
  Subdevice #30: subdevice #30 
  Subdevice #31: subdevice #31 
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback] 
  Subdevices: 8/8 
  Subdevice #0: subdevice #0 
  Subdevice #1: subdevice #1 
  Subdevice #2: subdevice #2 
  Subdevice #3: subdevice #3 
  Subdevice #4: subdevice #4 
  Subdevice #5: subdevice #5 
  Subdevice #6: subdevice #6 
  Subdevice #7: subdevice #7 
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 4: p16v [p16v] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: Generic [HD-Audio Generic], device 7: HDMI 1 [HDMI 1] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 2: Generic_1 [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0
[/FONT]
```
```
[FONT=monospace][COLOR=#000000]$ aplay -L [/COLOR]
null 
    Discard all samples (playback) or generate zero samples (capture) 
iec958 
    IEC958 (S/PDIF) Digital Audio Output 
hw:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    Direct hardware device without any conversions 
hw:CARD=Audigy2,DEV=2 
    SB Audigy 2 ZS [SB0350], Multichannel Capture/PT Playback 
    Direct hardware device without any conversions 
hw:CARD=Audigy2,DEV=3 
    SB Audigy 2 ZS [SB0350], Multichannel Playback 
    Direct hardware device without any conversions 
hw:CARD=Audigy2,DEV=4 
    SB Audigy 2 ZS [SB0350], p16v 
    Direct hardware device without any conversions 
plughw:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    Hardware device with all software conversions 
plughw:CARD=Audigy2,DEV=2 
    SB Audigy 2 ZS [SB0350], Multichannel Capture/PT Playback 
    Hardware device with all software conversions 
plughw:CARD=Audigy2,DEV=3 
    SB Audigy 2 ZS [SB0350], Multichannel Playback 
    Hardware device with all software conversions 
plughw:CARD=Audigy2,DEV=4 
    SB Audigy 2 ZS [SB0350], p16v 
    Hardware device with all software conversions 
default:CARD=Audigy2 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    Default Audio Device 
sysdefault:CARD=Audigy2 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    Default Audio Device 
front:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    Front output / input 
rear:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    Rear speakers 
center_lfe:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    Center and Subwoofer speakers 
side:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    Side speakers 
surround21:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    2.1 Surround output to Front and Subwoofer speakers 
surround40:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    4.0 Surround output to Front and Rear speakers 
surround41:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    4.1 Surround output to Front, Rear and Subwoofer speakers 
surround50:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    5.0 Surround output to Front, Center and Rear speakers 
surround51:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers 
surround71:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers 
iec958:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    IEC958 (S/PDIF) Digital Audio Output 
dmix:CARD=Audigy2,DEV=0 
    SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback 
    Direct sample mixing device 
dmix:CARD=Audigy2,DEV=2 
    SB Audigy 2 ZS [SB0350], Multichannel Capture/PT Playback 
    Direct sample mixing device 
dmix:CARD=Audigy2,DEV=3 
    SB Audigy 2 ZS [SB0350], Multichannel Playback 
    Direct sample mixing device 
dmix:CARD=Audigy2,DEV=4 
    SB Audigy 2 ZS [SB0350], p16v 
    Direct sample mixing device 
hw:CARD=Generic,DEV=3 
    HD-Audio Generic, HDMI 0 
    Direct hardware device without any conversions 
hw:CARD=Generic,DEV=7 
    HD-Audio Generic, HDMI 1 
    Direct hardware device without any conversions 
plughw:CARD=Generic,DEV=3 
    HD-Audio Generic, HDMI 0 
    Hardware device with all software conversions 
plughw:CARD=Generic,DEV=7 
    HD-Audio Generic, HDMI 1 
    Hardware device with all software conversions 
hdmi:CARD=Generic,DEV=0 
    HD-Audio Generic, HDMI 0 
    HDMI Audio Output 
hdmi:CARD=Generic,DEV=1 
    HD-Audio Generic, HDMI 1 
    HDMI Audio Output 
dmix:CARD=Generic,DEV=3 
    HD-Audio Generic, HDMI 0 
    Direct sample mixing device 
dmix:CARD=Generic,DEV=7 
    HD-Audio Generic, HDMI 1 
    Direct sample mixing device 
hw:CARD=Generic_1,DEV=0 
    HD-Audio Generic, ALC887-VD Analog 
    Direct hardware device without any conversions 
plughw:CARD=Generic_1,DEV=0 
    HD-Audio Generic, ALC887-VD Analog 
    Hardware device with all software conversions 
default:CARD=Generic_1 
    HD-Audio Generic, ALC887-VD Analog 
    Default Audio Device 
sysdefault:CARD=Generic_1 
    HD-Audio Generic, ALC887-VD Analog 
    Default Audio Device 
front:CARD=Generic_1,DEV=0 
    HD-Audio Generic, ALC887-VD Analog 
    Front output / input 
surround21:CARD=Generic_1,DEV=0 
    HD-Audio Generic, ALC887-VD Analog 
    2.1 Surround output to Front and Subwoofer speakers 
surround40:CARD=Generic_1,DEV=0 
    HD-Audio Generic, ALC887-VD Analog 
    4.0 Surround output to Front and Rear speakers 
surround41:CARD=Generic_1,DEV=0 
    HD-Audio Generic, ALC887-VD Analog 
    4.1 Surround output to Front, Rear and Subwoofer speakers 
surround50:CARD=Generic_1,DEV=0 
    HD-Audio Generic, ALC887-VD Analog 
    5.0 Surround output to Front, Center and Rear speakers 
surround51:CARD=Generic_1,DEV=0 
    HD-Audio Generic, ALC887-VD Analog 
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers 
surround71:CARD=Generic_1,DEV=0 
    HD-Audio Generic, ALC887-VD Analog 
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers 
dmix:CARD=Generic_1,DEV=0 
    HD-Audio Generic, ALC887-VD Analog 
    Direct sample mixing device
[/FONT]
```

i am hoping i can get 3 or 4 outputs and have speakers on my server in seveal rooms for use with my mpd server

---

