---
title: "alsamixer 1.2.9 works but when i put sudo alsamixer cannot open mixer: Host is down"
date: 2024-08-22
forum: Hardware
---

### Post by jimbean on 2024-08-22
when i run alsamixer, pipewire is my default card when i change the default card to HDMI [HDA Intel HDMI], it wont save after hitting ESC when i restart alsmixer it's pipewire again as default

aplay I
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [SONY TV]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

amixer -c0
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

alsamixer -c0 --view=All

the default card is HDMI [HDA Intel HDMI]
but it does not save to that when i type in just  plain alsamixer

this is a problem with my sound crackling and popping when a video plays for awhile and while moving mouse 
this is happening with ubuntu 24.04 lts it did not does not happen with ubuntu 22.04.4 lts

why does sudo alsamixer return with this comment: cannot open mixer: Host is down

thanks for try to read this

---

