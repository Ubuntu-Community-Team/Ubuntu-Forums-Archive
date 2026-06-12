---
title: "problem with microphone on HP t645uk"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by andy101 on 2006-10-25
Hi

I have a HP Pavilion t645uk with Ubuntu Linux 6.06 installed.

My computer has two sets of sound connections, one at the front and one at the back.

the rear set has audio out, line in and microphone sockets, the front has headphone, line in and microphone sockets.

The microphone socket on the front of the machine won't work. No sound is recorded from it when I connect my microphone. 

The rear socket works fine but is inaccessible, and as its a headset mic the headphone cable won't reach to the front (the rear audio goes to the monitor).

The front socket works fine in Windows (but I would rather not have to use windows)

My sound is provided by onboard RealTek ALC650 6-channel audio CODEC
subsystem (AC'97 2.2 compliant)


System Details:
[HP Pavilion t645uk web site ](http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&cc=us&dlc=&product=433051&)

[Motherboard Spec](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=&product=433051&docname=c00063272)

[PC Spec (PDF)](http://h10032.www1.hp.com/ctg/Manual/c00243431.pdf)

the wiki suggested checking /proc/asound/cards this contains
```

0 [ICH5           ]: ICH4 - Intel ICH5
                    Intel ICH5 with ALC650F at 0xfebff800, irq 209

```

arecord shows the following devices:
```

$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 2: Intel ICH - MIC2 ADC [Intel ICH5
- MIC2 ADC]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
 Subdevices: 1/1
 Subdevice #0: subdevice #0

```
Should it be listed 4 times? Is that once for each of the line in and
headphone sockets?

lspci -v gives:
```

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER
(ICH5/ICH5R) AC'97 Audio Controller (rev 02)
       Subsystem: ASUSTeK Computer Inc.: Unknown device 8095
       Flags: bus master, medium devsel, latency 0, IRQ 209
       I/O ports at d800 [size=256]
       I/O ports at dc00 [size=64]
       Memory at febff800 (32-bit, non-prefetchable) [size=512]
       Memory at febff400 (32-bit, non-prefetchable) [size=256]
       Capabilities: <available only to root>

```

ALSA's website suggests I need the snd-intel8x0 module.
lsmod lists snd_intel8x0 as already loaded.

Any ideas on how I can fix this, or find out whats wrong with it?
Any help gratefully received.

Thanks
-- Andy

---

