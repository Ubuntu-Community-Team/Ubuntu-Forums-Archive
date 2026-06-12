---
title: "sound problem with ALC660"
date: 2010-05-23
forum: Hardware
---

### Post by e_stoimenov on 2010-05-23
[SIZE=4][FONT=Comic Sans MS]Hi,
I have upgrade to Ubuntu 10.04LTS a few days ago :). Unfortunately I can't take no sound out. 
My soundcard is *ALC660*, but it is recognized as *VT1708A*. Below is the [/FONT][/SIZE]**[SIZE=4][FONT=Comic Sans MS]lspci -v | less[/FONT][/SIZE]**[SIZE=4][FONT=Comic Sans MS] command:
 
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed+
        Capabilities: [70] Subsystem: Device 4b73:907a

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel
        Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Kernel driver in use: k8temp
        Kernel modules: k8temp

02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device 8199
        Flags: bus master, fast devsel, latency 0, IRQ 24
        Memory at 20000000 (32-bit, non-prefetchable) [size=64M]
        Memory at d0000000 (64-bit, prefetchable) [size=128M]
        Memory at 24000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 25000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [128] Power Budgeting <?>
        Kernel driver in use: nvidia
        Kernel modules: nvidia-current, nvidiafb, nouveau

04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
:
[B]
aplay[/B] comes with "*no soundcard found*"
Also I tried updating the ALSA drivers to 1.0.23 with no success!!!
Any help please!!!!:sad:

REGARDS!!![/FONT][/SIZE]                                                                                                                                    *                                              Last edited by Many; May 15th, 2008 at 04:01 PM..                                                            *

---

### Post by e_stoimenov on 2010-06-05
I've solved the problem by removing the 64-bit version of Ubuntu and installing the 32-bit.

---

