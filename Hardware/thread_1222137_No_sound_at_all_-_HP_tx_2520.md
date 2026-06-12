---
title: "No sound at all - HP tx 2520"
date: 2009-07-24
forum: Hardware
---

### Post by bangolio on 2009-07-24
Hi,

Fresh ubuntu installation, laptop is HP Pavilion TX 2520 EJ, everything is working fine except for the sound which doesnt work at all.

Volume settings are fine.
I searched for similiar threads and only stumbled upon the ones with the acpi problem or with the sound working through the headphones jack but not the speakers.

```
$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Would appreciate any kind of help, thanks!

---

