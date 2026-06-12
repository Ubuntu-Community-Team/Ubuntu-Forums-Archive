---
title: "Audio interface doesn't turn on after suspend"
date: 2016-03-14
forum: Hardware
---

### Post by Bucky Ball on 2016-03-14
Hi all,

I have an old Hoontech DSP24 audio interface attached to my new desktop. Works fine, until I go into suspend. When I come out of suspend, all lights are off and sound is routed to the HDMI monitor instead of the audio interface. 

Any ideas how I can get this to wake up with the rest of the hardware after suspend?

Further info: the audio device is connected to its PCI soundcard on the motherboard. It is not a USB device. The device comes in two bits: the PCI card and the outboard, 8 channel audio interface. 

Just ask for any info. In the meantime, this is how my machine sees it:
```

*-multimedia
       description: Multimedia audio controller
       product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
       vendor: VIA Technologies Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=snd_ice1712 latency=32
       resources: irq:18 ioport:d040(size=32) ioport:d070(size=16) ioport:d060(size=16) ioport:d000(size=64)
```

Xubuntu-core 15.10, i7, GTX 970, 16Gb RAM.

TIA

* [This is it]("http://www.st-audio.de/products/dsp2000/info.html"). Yes, it's ancient! But works fine for my purposes and is FULLY supported in Ubuntu.

---

### Post by Bucky Ball on 2016-03-18
Le boomp.

---

