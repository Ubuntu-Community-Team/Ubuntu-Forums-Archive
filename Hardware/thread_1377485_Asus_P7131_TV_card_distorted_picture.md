---
title: "Asus P7131 TV card distorted picture"
date: 2010-01-10
forum: Hardware
---

### Post by mehturt on 2010-01-10
I am using Asus P7131 Hybrid TV card on Ubuntu 9.10.  I am able to tune all my analog channels but the display is distorted while watching TV.  Sometimes, however, it works fine and the picture is fine.  I was trying xawtv and mplayer and it looks the same.

```
$ lspci -v:
01:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
        Subsystem: ASUSTeK Computer Inc. Device 4876
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at fcfff800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: saa7134
        Kernel modules: saa7134
```

---

### Post by mehturt on 2010-01-11
More information:
Xawtv works fine right after boot.  I also have Mythtv installed, however analog channel scanning does not work there so I configured 2 channels that work fine in Xawtv.  However I am not able to watch tv via mythfrontend, I get an error: 
Error: Mythtv is using all inputs but there are no active recordings?
So I run mythtv-setup and I see the 2 channels configured there, so I exit that and mythfilldatabase is run.
Ever since then xawtv does not work fine anymore, the picture is distorted, screenshots after Print Screen are distorted as well.

---

