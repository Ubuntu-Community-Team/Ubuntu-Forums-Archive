---
title: "Sound problem with High Definition Audio"
date: 2008-09-12
forum: Hardware
---

### Post by alexmulo on 2008-09-12
Hi

Recently i have bought a new motherboard, an Asrock K10N78hSLI-GLAN, CPU AMD 64 X2 4850e and 2 GB RAM Vdata.

First I have installed Windows Vista and I heard a sound disturb when play a soud or a MP3. Than I have installed Ubuntu 8.04.1 and I have the same problem. Tha I try to install the new audio driver on Vista and the problem go away. 

Here in youtube I have uploded a video where it's possible to hear this sound disturb [http://www.youtube.com/watch?v=lyPU0yCYVNg](http://www.youtube.com/watch?v=lyPU0yCYVNg) .

I thin thath this is a motherboard hardware issue.


What do you think? What must I do?

---

### Post by Crafty Kisses on 2008-09-12
Post the results of this command:
```
lspci
```

---

### Post by alexmulo on 2008-09-12
the results are:

alex@alex-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075c (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0751 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0760 (rev a2)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0778 (rev a1)
00:12.0 PCI bridge: nVidia Corporation Unknown device 075b (rev a1)
00:13.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
alex@alex-desktop:~$

---

