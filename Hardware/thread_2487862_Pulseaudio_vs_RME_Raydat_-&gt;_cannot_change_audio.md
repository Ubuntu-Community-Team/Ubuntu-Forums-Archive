---
title: "Pulseaudio vs RME Raydat -&gt; cannot change audio card"
date: 2023-06-17
forum: Hardware
---

### Post by slavoy on 2023-06-17
Hello,

I use 2 RME professional PCIx audio cards in PC, Ubuntu 22.04 clean install (but was the same in previous versions), I can play sound from VLC thru ALSA via RME card, but I am not able to set the same card in Pulseaudio as a system default card. When I connect USB audio card, immediately this is displayed in devices and I can use it in Pulseaudio, but I cannot find both PCIe RME cards anywhere in Pulseaudio and I cannot switch to my main RME RayDat card. I see all card in Alsa. Can you kindly help me how to see all audio cards in Pulseaudio and be able to select.
Alsa see everything:
[IMG]http://www.slaveksamal.com/wp-content/uploads/2023/06/alsa.jpg[/IMG]
But only USB and one card is in system Pulseaduio:
[IMG]http://www.slaveksamal.com/wp-content/uploads/2023/06/pulse.jpg[/IMG]

The same from aplay -l
```
$ aplay -l
**** List of  PLAYBACK Hardwarových devices ****
karta 0: Default [RME RayDAT], za&#345;ízení 0: RME RayDAT [RME RayDAT]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 2: U192k [UMC204HD 192k], za&#345;ízení 0: USB Audio [USB Audio]
  Podza&#345;ízení: 0/1
  Podza&#345;ízení #0: subdevice #0
karta 3: HDSPe00000003 [RME AIO Pro_00000003], za&#345;ízení 0: RME AIO Pro [RME AIO Pro]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 4: NVidia [HDA NVidia], za&#345;ízení 3: HDMI 0 [HDMI 0]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 4: NVidia [HDA NVidia], za&#345;ízení 7: HDMI 1 [HDMI 1]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 4: NVidia [HDA NVidia], za&#345;ízení 8: HDMI 2 [HDMI 2]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 4: NVidia [HDA NVidia], za&#345;ízení 9: HDMI 3 [HDMI 3]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 4: NVidia [HDA NVidia], za&#345;ízení 10: HDMI 4 [HDMI 4]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 4: NVidia [HDA NVidia], za&#345;ízení 11: HDMI 5 [HDMI 5]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0

```
but list from pulseaudio is shorter:
```
pactl list sinks short
0	alsa_output.usb-BEHRINGER_UMC204HD_192k-00.analog-surround-40	module-alsa-card.c	s32le 4&#8239;ch 44100&#8239;Hz	IDLE
1	alsa_output.pci-0000_06_00.0.multichannel-output	module-alsa-card.c	s32le 16&#8239;ch 44100&#8239;Hz	SUSPENDED

```

Do you have any idea how to allow all available cards in Pulseaudio? I can use one of my RME cards, but everytime only RME AIO, I cannot switch to 2 card, RME RayDat under Pulsaudio. This is simply cannot be seen, it's hidden. It's not pci slot or master/slave (clock) synchronization, simply every time I can only see one RME card under Pulsaudio, only MRE AIO, but I can see everything in Alsa.

Many thanks in advance! I have to use USB card here in my studio for years in Dual boot machine and still have no idea how to solve all RME issues. It's better now, it works in Alsa , but still problems in Pulseaudio system. Sl.

---

