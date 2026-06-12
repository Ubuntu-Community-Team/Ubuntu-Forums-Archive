---
title: "[ASUS] Audio playing at the same time from speakers and headphones"
date: 2016-08-17
forum: Hardware
---

### Post by zangetsu94 on 2016-08-17
On my Asus, with Kubuntu 14.04, If I plug the headphones audio still plays form both outputs (speakers and headphones). I can fix this problem manually after the boot with alsamixer or Phonon, but it's irritating. I know this is a know issue and It was fixed on 16.04 release, but i can't upgrade to this version. So, how can I fix this problem?

```
lspci -nn | grep -i audio
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:9d70] (rev 21)

```
```
aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: PCH [HDA Intel PCH], dispositivo 0: ALC256 Analog [ALC256 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 7: HDMI 1 [HDMI 1]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 8: HDMI 2 [HDMI 2]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```
```
amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 60 [69%] [-20.25dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'

```
[http://i65.tinypic.com/20aou49.png](http://i65.tinypic.com/20aou49.png)

Solutions that I tried (without success):
[LIST]
[*]```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
[*]```
echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
[*]```
echo "options snd-hda-intel model=laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
[*]```
echo "options snd-hda-intel position_fix=1 enable=yes" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
[/LIST]

):P

---

### Post by os2 on 2016-08-18
In alsamixer there is an option called Automute. Enable that and one of the outputs will mute automatically.

---

### Post by zangetsu94 on 2016-08-20
Dear os2, have you read the OP before posting your advice? I think that your the answer is "no". I've attached a picture where AutoMute in alsamixer is clearly enabled.
Cheers :)

---

