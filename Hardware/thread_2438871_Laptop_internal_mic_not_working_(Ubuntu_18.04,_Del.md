---
title: "Laptop internal mic not working (Ubuntu 18.04, Dell M6800)"
date: 2020-03-19
forum: Hardware
---

### Post by mfry on 2020-03-19
I am trying to get my Dell Precision M6800 laptop's internal microphone   working on Ubuntu 18.04.  I've read a number of forum posts, but my   setup is not the same as those from which I've read.

When I run pavucontrol, the "Input Devices" tab shows the first attached image.
[ATTACH=CONFIG]285236[/ATTACH]
The second bar never registers any sound I make.

When I run alsamixer I get the second attached image, which doesn't seem to show any input device.
[ATTACH=CONFIG]285237[/ATTACH]
Other diagnostics:
     ```
$ arecord -l 

**** List of CAPTURE Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: ALC3226 Analog [ALC3226 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 2: ALC3226 Alt Analog [ALC3226 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
   
```
 $ lspci -v | grep -i mic
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
    Subsystem: Dell Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
    Subsystem: Dell 8 Series/C220 Series Chipset High Definition Audio Controller
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
    Subsystem: Dell GK104 HDMI Audio Controller
  
```
```
$ cat /proc/asound/card*  
 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7834000 irq 40
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7830000 irq 41
 2 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf5080000 irq 17

```

Hopefully that's enough info.

---

