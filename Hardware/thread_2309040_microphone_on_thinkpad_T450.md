---
title: "microphone on thinkpad T450"
date: 2016-01-07
forum: Hardware
---

### Post by louisJ on 2016-01-07
Hi

I run Ubuntu 14.04 on my laptop : Lenovo Thinkpad T450.
And if I plug my microphone (jack 3,5mm) I don't see it in the list of input audio devices.
Can you help me figure this out, I am working with a micro so it's really important to me.

Thanks

```
$ sudo lshw -c multimedia
  *-multimedia:0          
       description: Audio device
       product: Broadwell-U Audio Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:43 memory:e1230000-e1233fff
  *-multimedia:1
       description: Audio device
       product: Wildcat Point-LP High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:49 memory:e1234000-e1237fff



```

---

