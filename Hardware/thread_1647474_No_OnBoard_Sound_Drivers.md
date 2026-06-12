---
title: "No OnBoard Sound Drivers?"
date: 2010-12-17
forum: Hardware
---

### Post by Wader_WS on 2010-12-17
Hey there, im having trouble getting sound working on my install of 10.10. 

The motherboard is just a cheap'o Asus P5QPL-AM, trying to use the onboard.

here is the info from sudo lshw -c sound

>   *-multimedia UNCLAIMED
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe9fc000-fe9fffff


Cant see to find a suitable driver anywhere and asus dont supply any non-windows formats.

cheers for any help, Wader

---

### Post by IcarusR on 2010-12-17
Try adding 'model=your model' to /etc/modprobe.d/alsa-base.conf 
These two threads will help.

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

