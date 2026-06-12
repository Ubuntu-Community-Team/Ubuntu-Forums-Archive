---
title: "There is no sound with usb card line 6 guitar port on Ubuntu Studio 16.04.3"
date: 2017-09-18
forum: Hardware
---

### Post by lexaaladdin on 2017-09-18
When the system is turned on, the dell inspiron n5110 with Ubuntu studio 16.04.3 does not work usb sound card line 6 guitar port. There is absolutely no sound. Several occasional physical plugging / sticking of the usb plug (on all ports such) helps. One stick / poke can be small, the sound appears, but in addition to it there is still a squeak or crack in the rhythm of the music, it is exactly 2-5 times to reconnect the card. I result different settings.


In the volume control, as you can see, it is shown that the music is playing.
[https://ibb.co/b35hR5](https://ibb.co/b35hR5)
[https://ibb.co/nC4bm5](https://ibb.co/nC4bm5)
[https://ibb.co/kyo2R5](https://ibb.co/kyo2R5)


In alsamixer also seen.
[https://ibb.co/iBAP65](https://ibb.co/iBAP65)


Output commands:


lexaaladdin @ n5110: ~ $ lspci | grep Audio
00: 1b.0 Audio device: Intel Corporation 6 Series / C200 Series Chipset Family High Definition Audio Controller (rev 05)
01: 00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
lexaaladdin @ n5110: ~ $
There's no my card.


lexaaladdin @ n5110: ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: 92HD87B1 / 3 Analog [92HD87B1 / 3 Analog]
  Subdevices: 1/1
  Subdevice # 0: subdevice # 0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice # 0: subdevice # 0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice # 0: subdevice # 0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice # 0: subdevice # 0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice # 0: subdevice # 0
card 2: GuitarPort [GuitarPort], device 0: GuitarPort [GuitarPort]
  Subdevices: 0/1
  Subdevice # 0: subdevice # 0
lexaaladdin @ n5110: ~ $
There is.


In dmesg there are strange moments with errors:
[https://ibb.co/jqJYzQ](https://ibb.co/jqJYzQ)

---

### Post by lexaaladdin on 2017-09-19
[https://pastebin.com/BuU2NyMS](https://pastebin.com/BuU2NyMS)

---

