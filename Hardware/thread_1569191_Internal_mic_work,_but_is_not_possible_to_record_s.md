---
title: "Internal mic work, but is not possible to record sound, 10.04"
date: 2010-09-06
forum: Hardware
---

### Post by ivra on 2010-09-06
Hi,

I have new problem for me. My laptop-internal mic work and I can hear my own voice in the speakers, but I can't record sound or use Skype.

Codec: Realtek ALC883
Codec: LSI Si3054

0 snd_hda_intel

0 [SB             ]: HDA-Intel - HDA ATI SB
                     HDA ATI SB at 0xfebf8000 irq 16

card  0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card  0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card  0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


options snd-hda-intel model=3stack-2ch-dig (3-jack with SPDIF I/O (ALC883) )

When I try the Live CD 10.04 - mic and record sound work perfect. I control the level of the mic from alsamixer.

Sorry for my English. If somebody can help thanks.

---

### Post by ivra on 2011-05-14
Hi,

I found that if I put in alsa-base.conf the line: options snd-hda-intel position_fix=1 my internal mic start to work.

I hope this fix my problems and to continue to work without bugs.

---

