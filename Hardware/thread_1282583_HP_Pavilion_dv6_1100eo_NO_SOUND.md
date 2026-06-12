---
title: "HP Pavilion dv6 1100eo NO SOUND"
date: 2009-10-04
forum: Hardware
---

### Post by fimas on 2009-10-04
Hello everyone!

I've searched the forum on how to get the sound working on a HP Pavilion dv6 1100eo, but I've had no success. I've updated alsa to the latest version, 1.0.21 and double, triple, quadruple checked the volume controls to see if anything is muted; nothing is. I also tried aplay -l to see if the sound card was recognized. 

```
christian@christian-laptop:~$ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: SB [HDA ATI SB], enhet 0: STAC92xx Analog [STAC92xx Analog]
  Underordnade enheter: 0/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: SB [HDA ATI SB], enhet 1: STAC92xx Digital [STAC92xx Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: HDMI [HDA ATI HDMI], enhet 3: ATI HDMI [ATI HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
```

I did find a thread about "[SOLVED] No sound: Toshiba Satellite a135-s2386"

[http://ubuntuforums.org/showthread.php?t=452992&highlight=](http://ubuntuforums.org/showthread.php?t=452992&highlight=)[SOLVED]+No+sound%3A+Toshiba+Satellite+a135-s2386

Which uses a ATI SB card. And tried to add the line 

```
options snd-hda-intel position_fix=1 model=3stack
```

into /etc/modprobe.d/alsa-base. It also said that a couple of reboots were necessary, which I also did. But it did not fix the problem.

Oh and I run Ubuntu 9.04 and I have updated everything to latest version, according to Package Manager. 

Any help will be greatly appreciated!

Note! I upgraded to Ubuntu 9.10 Karmic because a Alsa tutorial said the new kernel could solve the hardware issue.

---

