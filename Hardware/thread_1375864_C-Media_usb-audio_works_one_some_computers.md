---
title: "C-Media usb-audio works one some computers"
date: 2010-01-08
forum: Hardware
---

### Post by samuelt on 2010-01-08
I have usb soundcard that works one two out of three computers. All of them running diffrent versions of ubuntu.

The Device:
From lsusb: 0d8c:000c C-Media Electronics, Inc. Audio Adapter
It seems to have a C-Media chip and be supported.

It works on these two machines:
1) laptop, x86, 9.10. Stock kernel.
2) tower, x86, 8.10. Stock kernel. [alsa-info.sh output]("http://thollander.net/upload/works")

It does not work on:
1) SheevaPlug (arm, 9.04). Not a stock kernel, see below.
uname -a: Linux otto 2.6.30.2 #11 PREEMPT Wed Jul 22 19:53:31 MDT 2009 armv5tel GNU/Linux
[alsa-info.sh output]("http://thollander.net/upload/dont-work")

I have tried loading snd-usb-audio both with the vid & pid options according to the lsusb output and without them.
Then the soundcard is detected and usable but the sound coming out is just noise.
aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have tried to let it be detected it on its own.
Then the soundcard is detected but not usable.
aplay -l gives this: aplay: device_list:221: no soundcard found

Installing alsa-source and using it with module-assistant will require significant yak-shaving, which I'd like to avoid if possible.

Any suggestions?

---

