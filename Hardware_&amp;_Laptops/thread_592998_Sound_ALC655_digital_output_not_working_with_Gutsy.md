---
title: "Sound: ALC655 digital output not working with Gutsy?"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by IndieRockSteve on 2007-10-26
after installing Gutsy I can't get digital output to work with my ALC655 (via the NVidia CK804). it worked fine with my previous Kanotix install, i could pass stereo PCM and AC3. now if I choose ALSA:Digital I get nothing. if I set it to ALSA:Analog it works but AC3 is downmixed to stereo and if I specify to use the SPDIF (ie -ac hwac3 in mplayer) i just get that digital cackle through the headphones.

I've got my asound.conf specifying that digital should use device 2 which from aplay -l looks right:
> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


anyone have any ideas?

---

### Post by Mike5 on 2007-10-28
Same problem here with ALC850 via nVidia CK804. With Feisty I had the SPDIF working fine. After having installed Gutsy, SPDIF is mute. I have tried every and each of the alsamixer configuration options. The strange thing is that the amplifier lights on the digital led, but outputs no sound.

There must be something broken (perhaps in the new ALSA version) when using on-board sound cards with nVidia Force4. My MoBo is an Asus A8N-SLI.

Michele

---

