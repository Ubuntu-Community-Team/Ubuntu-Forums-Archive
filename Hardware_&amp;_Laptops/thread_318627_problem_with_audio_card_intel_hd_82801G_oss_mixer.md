---
title: "problem with audio card intel hd 82801G oss mixer"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by suoko on 2006-12-14
hi,

I'm experiencing problems with the audio card of my laptop.
SPecifically the problem is with the oss mixer.
Volume of oss mixer is wither max or mute. Plus, the "line in" controller affects the overall audio volume, i.e. if I set it in the middle the overall audio is very high, while if I move it from the middel position it is very low.
Moreover, the "line in" controller affects the headphone exit. middle position -> it works, else it doesn't

Anybody else with this issue???

---

### Post by matt_risi on 2007-02-13
I'm also having problems with this card on my laptop, although slightly different. i get sound, but my headphone jack doesn't work. I researched ALSA and found that there is currently no driver developed for the card. Is there any workarounds for this that anyone's encountered?

---

### Post by dom on 2007-02-26
I have this card also in my new inspiron 9400, sound worked i'm sure, but now, logged in, want to use the audio and i'm getting nothing....

Details :
```

>lspci
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

>lspci -v
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Unknown device 01cd
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)


>lspci -v -n
00:1b.0 0403: 8086:27d8 (rev 01)
        Subsystem: 1028:01cd
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)

>cat /proc/asound/card0/codec#0 |grep -i codec
Codec: SigmaTel STAC9200

>cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).

>aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


```


I'm just after finding this post also, will try this out  [http://ubuntuforums.org/showthread.php?p=1742116](http://ubuntuforums.org/showthread.php?p=1742116)

Ok, just tried the headphones, and *they do* work !!!

Removing and even fiddling it in the audio jack (very delicate remember if you do this) done nothing to remedy the situation.

I rebooted and the audio works, so I guess it was something to do with audio drivers, rather than a stuck headphone jack switch. Remember, this is a brand new device, there has been headphone usage only twice now.

---

