---
title: "Problem with Audio device Intel Corporation 82801I (ICH9 Family) HD Audio Controller"
date: 2009-06-28
forum: Hardware
---

### Post by jayarbie on 2009-06-28
Hi everybody,

I have an ASUS X5DIJ-SX018L (K50) with Ubuntu 9.04 and the Audio device Intel Corporation 82801I (ICH9 Family) HD Audio Controller. The sound doesn't work at all. I tried pretty much, but so far nothing worked.

hwinfo:

PCI 1b.0: 0403 Audio device
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_293e
  Unique ID: u1Nb.0BStUO5UoL0
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x1111 "Santa Cruz Operation"
  SubDevice: pci 0x1043
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfdef4000-0xfdef7fff (rw,non-prefetchable)
  IRQ: 22 (5316 events)
  Module Alias: "pci:v00008086d0000293Esv00001111sd00001043bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

I also tested a suggestion to add an option "options snd-hda-intel probe_mask=x" with the values changing from 0 to 3 to the /etc/modprobe.d/alsa-base.conf - unfortunately without success.

Are there any ideas?

Thanks in advance, J

---

### Post by MadJester on 2009-06-28
Got sound by following the driver instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

---

### Post by karthik17 on 2009-09-05
I have recently bought a dell laptop, which has the same audio device Intel 82801I (ICH9 Family) , and I am also facing the same audio problem.

While searching the net, I read somewhere that if the webpage [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel) doesnot contain the audio device we have, it wont be supported by ubuntu. Is that true ? What will be the solution for this?

Please help us out !!!

---

