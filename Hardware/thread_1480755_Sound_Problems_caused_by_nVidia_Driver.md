---
title: "Sound Problems caused by nVidia Driver?"
date: 2010-05-11
forum: Hardware
---

### Post by rnelson0 on 2010-05-11
Hi All,

I've had sound issue on my media center ever since 8.10. I've tried all sorts of ways from this forum to fix it, but nothing worked. What always urked me, was that sound would always work in the live version of ubuntu, but it would stop after I installed it. I even tried buying a separate sound card that I KNEW was compatible with ubuntu to bypass my mobo's sound. Still nothing.

But I've just discovered something when installing 10.04. When I install the latest nVidia driver through the Hardware Drivers application and restart... my audio STOPS working. When I uninstall it, it WORKS! I install nVidia's driver, it STOPS again, uninstall it, it WORKS!

Has anyone else come across this? If so, how can I have both the nVidia driver and continue to have my sound work? This is a media center running XBMC (or maybe Boxee). Do I even need the nVidia driver?

For reference, here is info about my sound hardware and video hardware:

Sound (C-Media is the stand alone card I just installed, the other is onboard):
```

**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


Video:
```

lspci | grep VGA

02:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)

```

---

### Post by rnelson0 on 2010-05-12
I can't be the first one to experience this can I? Anyone?

---

