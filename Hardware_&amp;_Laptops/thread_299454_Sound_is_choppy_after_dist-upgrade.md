---
title: "Sound is choppy after dist-upgrade"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by djvishnu on 2006-11-14
I dist-upgraded the other day, and now I am having trouble with sound. It works fine until the cpuload rises, then it sounds like all sounds are chopped up, like the driver is interrupted or something. Sounds awful. I can record a sample if it'll help.

Have anyone heard of this probelm before, or know where to start looking for a fix?

Yhis is what lshw says about my audio hardware:
```

        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:de400000-de403fff irq:82

```

---

### Post by drphilngood on 2006-11-14
The [Comprehensive Sound Problem Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449") is where I'd start looking for a solution.:-k 

Hope this helps!:)

---

