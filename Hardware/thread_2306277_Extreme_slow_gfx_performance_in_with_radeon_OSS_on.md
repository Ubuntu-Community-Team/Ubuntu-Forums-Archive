---
title: "Extreme slow gfx performance in with radeon OSS on desktop"
date: 2015-12-14
forum: Hardware
---

### Post by stephan4 on 2015-12-14
Hi all, 



I use the actual Ubuntu 15.10 64bit edition and installed the whole OS freshly and have some issues.

Hardware: i7 4770K, and AMD R9 290X

_*What I did:*_ After the fresh OS installation and the standard updates via terminal, I switched via System properties menu to the fglrx-updates drivers...worked well but Steam Games were
stuttering and some guys advertised me to try the OSS radeon drivers due to some known problems with the fglrx drivers. So ...I switched back to the radeon OSS drivers via the System properties menu again and did nothing than wait for the system. Worked fine until reboot.
[I][U]
Situation: [/U][/I]Performance is now awfully slow, begins with a "frame by frame" feeling while starting grub and the login screen, also the desktop experience is extreme slow, literally I see each frame building up in seconds...not possible to work with it (note: after the fresh install, the oss radeon driver are set as standard and everything worked fine in the first instance). So, I switched back to the fglrx drivers via the menue (no manuall installation) and system runs fine again. 
[I][U]
Question[/U][/I]: Is there a way to use the non prop. OSS radeon drivers again without above problems. Some sort of reconfiguration? 


Actual lspci output with prop.driver: 
```
sudo lspci -vk
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii XT [Radeon R9 290X] (prog-if 00 [VGA controller])
    Subsystem: Hightech Information System Ltd. Device 2342
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=8M]
    I/O ports at e000 [size=256]
    Memory at f7e00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at f7e40000 [disabled] [size=128K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Capabilities: [270] #19
    Capabilities: [2b0] Address Translation Service (ATS)
    Capabilities: [2c0] #13
    Capabilities: [2d0] #1b
    Kernel driver in use: fglrx_pci
```

```
glxinfo | head
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
```
[COLOR=#000000]Would like to give you guys the same output with the open source drivers but it is not possible to work with it, and as I mentioned above, after the fresh install the open source driver were working.[/COLOR]

---

