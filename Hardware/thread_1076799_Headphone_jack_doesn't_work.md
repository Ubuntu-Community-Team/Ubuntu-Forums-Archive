---
title: "Headphone jack doesn't work"
date: 2009-02-21
forum: Hardware
---

### Post by riddix on 2009-02-21
Hello!


I'm using Ubuntu Studio 8.10 x64 on an ASUS Z37S. 

My problem is if i plug in headphones the notebook speakers correctly mute but there is no sound in the headphones. On Win XP it works fine. Some Infos: 

```
cat /proc/asound/cards

 0 [Intel          ]: HDA-Intel - HDA Intel

                      HDA Intel at 0xf3ff8000 irq 21
```

```
lshw -C sound

  *-multimedia            

       description: Audio device

       product: 82801H (ICH8 Family) HD Audio Controller

       vendor: Intel Corporation

       physical id: 1b

       bus info: pci@0000:00:1b.0

       version: 03

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list

       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

Thanks for any suggestions you can pass along.

---

### Post by markbuntu on 2009-02-21
Look in here, there is a section about the snd-hda-intel driver:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

