---
title: "Trying to get sound through HDMI"
date: 2011-12-16
forum: Hardware
---

### Post by jarrett on 2011-12-16
Hi,
So I have fought this for several hours tonight, now I officially give up trying to figure this one out by myself.
I have eeebox 1501P which I'm trying to get sound through HDMI on.

cat /proc/asound/cards says
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 20
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfbef8000 irq 16

```

aplay -l says
```
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and when I run alsamixer and change cards (F6) to HDA NVidia it says 'This sound device does not have any controls'.
What to do?

---

