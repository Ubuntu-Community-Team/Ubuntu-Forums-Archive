---
title: "Front Audio Problems (FAP)"
date: 2010-08-24
forum: Hardware
---

### Post by brickhead248 on 2010-08-24
Hey Ubuntu forums! I've had a huge bout of problems with my new laptop (Acer Aspire TimelineX 5820TG-524G50MN) dual-booting W7-64 and Ubuntu 10-4 64

so I'll start a different thread for each problem. 

Firstly, the front audio!

Music plays fine on the speakers, but when i plug earphones into the front audio jack, the audio shuts off on the speakers, but is not switched to the earphones.

Obviously, everything works fine in Windows 7, so this is a software thing.

Here are the devices in lshw:

        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:dc500000-dc503fff
           *-multimedia
                description: Audio device
                product: Redwood HDMI Audio [Radeon HD 5600 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:dc420000-dc423fff

I didn't notice any IRQ conflicts (but i could probably have looked harder).
The only audio outs i have are HDMI, speakers and front 3.5mm audio.

Any ideas at all? I have no idea where to start.

Thanks!

---

### Post by brickhead248 on 2010-09-02
Here's the solution:

upgrade ALSA: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

EVERYTHING WORKS

also, if you have a Acer TimelineX then i would suggest having a look at this thread
[http://ubuntuforums.org/showthread.php?t=1495123](http://ubuntuforums.org/showthread.php?t=1495123)

helped me fix so many problems!

---

