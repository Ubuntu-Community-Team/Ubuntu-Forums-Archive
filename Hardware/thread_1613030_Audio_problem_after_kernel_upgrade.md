---
title: "Audio problem after kernel upgrade"
date: 2010-11-03
forum: Hardware
---

### Post by Apapousek on 2010-11-03
Hello all,

I've recently upgraded my Linux kernel to 2.6.36 (compiled myself, which may be the problem) and my audio has been acting very odd.

During startup, if I have no headphones plugged in, the speakers on my laptop work just fine. But, if i plug a pair in, they will not work. If I start up my laptop with headphones plugged in, the headphones will work but not the speakers.

Could this be a problem with ALSA/other sound?

A simple lshw command showed this for my audio hardware:

multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:d2400000-d2403fff

Thanks,
Anthony P.

---

