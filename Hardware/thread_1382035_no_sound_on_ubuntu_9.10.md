---
title: "no sound on ubuntu 9.10"
date: 2010-01-15
forum: Hardware
---

### Post by vitaly87 on 2010-01-15
hello!
after i did an update to 9.10,. my ubuntu cant find the sound card! what can i do? my audio is

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8290
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at dfef8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


and i have some problems on my hp 4900, i put the cd of 9.10 and when i get to the prepare partitions it just empty

---

### Post by some-what-Gnu-2-networks on 2010-01-15
make sure you have "gnome-alsamixer" installed and all devices are unmuted from their. I had this problem after switching to Xcfe

---

### Post by vitaly87 on 2010-01-16
ok i get this program but when i open it it is just empty. what can i do?

---

### Post by some-what-Gnu-2-networks on 2010-01-18
try installing libasound2 and libasound2-plugins
To be honest I'm not sure why that is empty.If this doesn't work, at least I gave you a bump.;)

---

