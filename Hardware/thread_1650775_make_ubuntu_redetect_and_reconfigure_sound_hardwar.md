---
title: "make ubuntu redetect and reconfigure sound hardware"
date: 2010-12-22
forum: Hardware
---

### Post by alex_ivaylov on 2010-12-22
Hi Guys,

I am still new and this is my first post here, so bear with me.

I installed Ubuntu 10.10 Desktop like a month ago and it didnt detect the built in Realtek sound card. 

After two weeks of attempts to install the drivers for it, I was told that the Realtek card is just not linux-friendly and I should get some better sound card.

So I bought a new c-media card which is one of the most popular cards now a days. Then I installed it and it's working on Windows but it doest work on the ubuntu installation.

In the devices sections, I cant see the card and I only have "Dummy Output" only.

If I check, I can see the card is detected:

```

root@webdev:~# cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfbefc000 irq 25
 1 [CMI8738        ]: CMI8738 - C-Media CMI8738
                      C-Media CMI8738 (model 37) at 0xe800, irq 17

```Also

```

alex@webdev:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```So you can see that the cmedia card is detected, but it doesnt show under the mixer's output devices.

I started Ubuntu using the Live CD and the sound was working perfectly and the devices were showing under the mixer settings.

Do you guys have any idea how to get the sound?

Thank you very much,
Alex

---

