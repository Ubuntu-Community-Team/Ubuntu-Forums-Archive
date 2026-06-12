---
title: "Conexant HD audio not producing any sound"
date: 2008-08-27
forum: Hardware
---

### Post by tchebichev on 2008-08-27
I am running Hardy Heron on an Intel core2duo machine and Ubuntu will not produce any sound (everything else works fantastically well).

I have a Toshiba laptop (Satellite P100-403). The audio card is a Conexant HD audio and it does not produce any sound at all. I read several posts about this specific problem, which seems to be well known, but nothing I read, including reinstalling Alsa drivers, seems to work for me.

The sound is working fine with Windows XP, and I checked the mixer is not muted. Here are some data :

1. lspci output (selected line)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

2. Kernel version
2.6.24-19-generic

3. aplay -l output
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

4. grep Codec /proc/asound/card0/codec#* output
Codec: Conexant CX20551 (Waikiki)

Any help will be appreciated.

Arnault, 'ubuntu@myarnault.net'

PS I should mention I posted this in Linuxquestions.org earlier but did not get any valid answer

---

