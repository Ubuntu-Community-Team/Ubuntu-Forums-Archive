---
title: "New Dell XPS 13 Intel Arc won't recognize external monitors"
date: 2024-07-19
forum: Hardware
---

### Post by eagledrc2 on 2024-07-19
Hi all. I bought a new Dell XPS 13 9340, specs below. How can I get it to recognize the external monitors?

It came w/ Windows 11. I tried Ubuntu 24.04 and had an issue with flashing colored lines across the screen, which I think was caused by the refresh rate. I replaced the install with 22.04 and it solved that problem - the refresh rate is now 77 hz which wasn't an option previously. 

But now my external monitor won't work. Its plugged in through a dock. I think the issue lies with the graphics card not the dock. One external monitor worked in 24.04 but not the other. Didn't troubleshoot much since the main display was such a problem. 

All the solutions I can find online are for nvidia drivers so I'm hoping I can get some help here. If it would be easier to reinstall 24.04 and fix the refresh rate, I'll happily do that. 

What I've tried in 22.04 to recognize the monitor:
-change WaylandEnable to false
-running xrandr only shows the built-in display
-install compiz and uncheck 'detect displays'

Dell XPS 13 9340
Intel Core Ultra 7 155H x 22
Intel Arc Graphics

Dock is a Dell TB16, one monitor plugged in via DP and the other HDMI. The HDMI is the one that worked on the 24.04 install. The dock is plugged into the computer via USB-C.

Ubuntu 22.04 LTS kernel 6.5

lspci output:
```
0000:00:00.0 Host bridge: Intel Corporation Device 7d01 (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation Device 7d55 (rev 08)
0000:00:04.0 Signal processing controller: Intel Corporation Device 7d03 (rev 04)
0000:00:05.0 Multimedia controller: Intel Corporation Device 7d19 (rev 04)
0000:00:06.0 System peripheral: Intel Corporation Device 09ab
0000:00:07.0 PCI bridge: Intel Corporation Device 7ec4 (rev 10)
0000:00:07.3 PCI bridge: Intel Corporation Device 7ec7 (rev 10)
0000:00:08.0 System peripheral: Intel Corporation Device 7e4c (rev 20)
0000:00:0a.0 Signal processing controller: Intel Corporation Device 7d0d (rev 01)
0000:00:0b.0 Processing accelerators: Intel Corporation Device 7d1d (rev 04)
0000:00:0d.0 USB controller: Intel Corporation Device 7ec0 (rev 10)
0000:00:0d.2 USB controller: Intel Corporation Device 7ec2 (rev 10)
0000:00:0d.3 USB controller: Intel Corporation Device 7ec3 (rev 10)
0000:00:0e.0 RAID bus controller: Intel Corporation Device 7d0b
0000:00:12.0 Serial controller: Intel Corporation Device 7e45 (rev 20)
0000:00:14.0 USB controller: Intel Corporation Device 7e7d (rev 20)
0000:00:14.2 RAM memory: Intel Corporation Device 7e7f (rev 20)
0000:00:15.0 Serial bus controller: Intel Corporation Device 7e78 (rev 20)
0000:00:15.2 Serial bus controller: Intel Corporation Device 7e7a (rev 20)
0000:00:16.0 Communication controller: Intel Corporation Device 7e70 (rev 20)
0000:00:1c.0 PCI bridge: Intel Corporation Device 7e3f (rev 20)
0000:00:1e.0 Communication controller: Intel Corporation Device 7e25 (rev 20)
0000:00:1f.0 ISA bridge: Intel Corporation Device 7e02 (rev 20)
0000:00:1f.3 Multimedia audio controller: Intel Corporation Device 7e28 (rev 20)
0000:00:1f.4 SMBus: Intel Corporation Device 7e22 (rev 20)
0000:00:1f.5 Serial bus controller: Intel Corporation Device 7e23 (rev 20)
0000:39:00.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
0000:3a:01.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
0000:3a:04.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
0000:3c:00.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
0000:3d:01.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
0000:3d:04.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
0000:3e:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller
0000:71:00.0 Network controller: Intel Corporation Device 272b (rev 1a)
10000:e0:06.0 PCI bridge: Intel Corporation Device 7e4d (rev 20)
10000:e1:00.0 Non-Volatile memory controller: SK hynix Device 1d59 (rev 03)

```

---

### Post by Yellow Pasque on 2024-07-20
You're going to need force_probe option for kernel 6.5
[https://ubuntuforums.org/showthread.php?t=2495988](https://ubuntuforums.org/showthread.php?t=2495988)

Don't be surprised if you run into the same issues you had with Ubuntu 24.04 once you do that.

> lspci output
It's not very readable. At least run:
```
sudo update-pciids
```

---

### Post by zzento on 2024-08-16
I'm using same hardware and can't get video via DisplayPort. Only HDMI works. Tried force_probe option with no joy using TB16 and WD22TB4 docks. @eagledrc2, did you manage to get any improvement?

---

