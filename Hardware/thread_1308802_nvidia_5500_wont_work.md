---
title: "nvidia 5500 wont work"
date: 2009-10-31
forum: Hardware
---

### Post by buzzmandt on 2009-10-31
I have an nvidia 5500 fx and karmic 9.10 and cannot get it to work.
```
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

```
I have tried the hardware drivers gui with ubuntu, same result (see below)
I have tried manual install of 185 driver, same result
I have tried the installer and driver from nvidia.com, same result

My result is a garbled screen that is usless flashing lines.  The first splash comes up fine, screen fickers, then goes garbage.

Picture from phone attached

I have tried several combinations and ways for setting a xorg.conf.  I'd paste mine but it is currently blank as nothing but that is working.

any suggestions?


```
buzzmandt@buzzmain:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
buzzmandt@buzzmain:~$

```

```
buzzmandt@buzzmain:~$ uname -a
Linux buzzmain 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
buzzmandt@buzzmain:~$

```

---

### Post by iWolf on 2009-10-31
Please submit a bug report

---

