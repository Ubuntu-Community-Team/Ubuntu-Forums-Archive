---
title: "Install Mini Pcie in Jetson Tk1"
date: 2014-08-12
forum: Hardware
---

### Post by djaniel on 2014-08-12
Hi!

I'm trying to run my wireless adapter in my embedded computer running Ubuntu 14.04 (Nvidia's Jetson TK1 Kernel: 3.10.24). The adapter is a miniPCIe board 7260 hmw. I was thinking that Ubuntu didn't have the correct drivers and tried unsuccessfully to install iwlwifi.
Later I discovered that under /lib/firmware I had three interesting files:

[LIST]
[*]iwlwifi-7260-7.ucode
[*]iwlwifi-7260-8.ucode
[*]iwlwifi-7260-9.ucode
[/LIST]
These files made me think that iwlwifi is already installed. Then, I ran "lspci -v". Result:

```
Network controller: Intel Corporation Wireless 7260 (rev 73)
subsystem: Intel corporation dual band wireless-ac 7260
flags: bus master, fast devsel, latency 0, IRQ 130Memory at 32200000 (64 bit, non-prefetchable)[ size = 8K]
Capabilities: <access denied>
```

The last line intrigues me and "Kernel driver in use" is not displayed. So, my best guess is that I only have to add permissions and assign a driver that is already available in my computer, but how do I do that?

If I'm wrong, I'd appreciate your assistance.

---

