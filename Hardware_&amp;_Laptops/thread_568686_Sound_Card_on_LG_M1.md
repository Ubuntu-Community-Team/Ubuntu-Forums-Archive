---
title: "Sound Card on LG M1"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by java.jfan on 2007-10-06
Hi, I'm running Ubuntu 7.04 on my LG M1 laptop.

I've noticed a minor problem with my sound card:
The problem is that I can't control volume _separately_ on my speakers and headphones.
Sound control applet works fine (PCM and Front controls inside the Playback tab) but it influences both speakers and headphones sound level.

The lspci's output relevant to my sound card is:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Thanks in advance for any help

---

### Post by java.jfan on 2007-10-06
Some additional output that can be useful...
aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v | grep -A 5 Audio:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: LG Electronics, Inc. Unknown device 0040
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at da400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

uname -r:
2.6.20-16-generic

---

### Post by java.jfan on 2007-12-30
Hi, I've found the answer here

[http://ubuntuforums.org/showthread.php?t=616845&highlight=HDA](http://ubuntuforums.org/showthread.php?t=616845&highlight=HDA)

Thanks a lot in any case

---

