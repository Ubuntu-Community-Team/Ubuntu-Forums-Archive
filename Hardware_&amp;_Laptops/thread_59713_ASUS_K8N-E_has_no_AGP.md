---
title: "ASUS K8N-E has no AGP?"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by fredrik on 2005-08-25
Having tried to get the latest ATI Radeon drivers to work with no luck for the last couple of days I tried to dig deeper why so. I found that there where some troubles with the AGP and here's what my Xorg.log says;
```
fredrik@ubuntu:~$ grep agp /var/log/Xorg.0.log      
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
```
I googled on this error and found the following on the official ATI site;
```
This is not a problem with the display driver.
First make sure that agpgart is loading properly.
To find out which AGP controller your motherboard uses, issue the following command:   lspci | grep AGP 

```
OK lets see what AGP controller I use then;
```

fredrik@ubuntu:~$ lspci | grep AGP
fredrik@ubuntu:~$

```
hmm wtf? As you can see I dont even have an AGP controller initilized which might explain why I had big time troubles trying to get the drivers to work. Any ideas what to do? Heres a full output of my lspci;
```

fredrik@ubuntu:~$ lspci
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4a49
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4a69
0000:02:07.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
0000:02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:02:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:02:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

```

---

