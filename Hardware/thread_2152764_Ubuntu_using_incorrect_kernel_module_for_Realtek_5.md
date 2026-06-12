---
title: "Ubuntu using incorrect kernel module for Realtek 5289 SD Card Reader"
date: 2013-06-08
forum: Hardware
---

### Post by Tronman on 2013-06-08
Hi everyone,

I have a Realtek SD card reader, Device 5289. I just tried my first SD card in Ubuntu earlier today to discover it couldn't read the card.

After some research, I stumbed upon this:

[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876)

Which seems to describe my hardware and issue perfectly.

I followed all the steps in the ticket, installed rts_bpp, (including creating the /lib/udev/rules.d/81-udisks-realtek.rules file), but my card reader still isn't working.

I believe I've narrowed down the problem, but I'm not sure the next step. Here's my output from lspci:

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 1587
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f7800000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rtsx_pci
	Kernel modules: rts_bpp, rtsx_pci

As you can see, the rts_bpp module seems to be installed fine (I also added it to /etc/modules), but Ubuntu keeps on insisting to use the rtsx_pci driver instead of the rts_bpp driver. I did manage to get it to use the rts_bpp driver once (by carefully unloading rtsx_pci and loading rts_bpp in the correct order), and my SD Card reader worked fine at that point (lspci reported the Kernel driver in use was rts_bpp), but then upon reboot, it went back to using the rtsx_pci driver and no longer worked.

So my question is: How do I get it to use rts_bpp instead of rtsx_pci, and stay that way upon reboot? I even tried adding rtsx_pci to /etc/modprobe.d/blacklist.conf, but alas, it just keeps loading!

Any help would be apprecaited! Thanks.

---

