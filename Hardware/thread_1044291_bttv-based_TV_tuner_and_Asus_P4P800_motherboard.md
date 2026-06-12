---
title: "bttv-based TV tuner and Asus P4P800 motherboard"
date: 2009-01-19
forum: Hardware
---

### Post by xingmu on 2009-01-19
I cannot detect my TV tuner card with mythbuntu (Hardy Heron).  

The TV tuner is Leadtek WinFast 2000 XP and is supported by the [bttv driver]("http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv"). 

The card is listed in the output of lspci
> 02:0d.0 Multimedia video controller: Brooktree Corporation Unknown device 034e (rev 11)
	Subsystem: LeadTek Research Inc. Unknown device 6609
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at faf00000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>

02:0d.1 Multimedia controller: Brooktree Corporation Unknown device 0858 (rev 11)
	Subsystem: LeadTek Research Inc. Unknown device 6609
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at faf01000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>


But when I attempt to modprobe bttv, it does not detect any card.  No device is assigned.  The relevant output from dmesg is only two lines:
> [  757.695711] bttv: driver version 0.9.17 loaded
[  757.695721] bttv: using 8 buffers with 2080k (520 pages) each for capture

I believe I should get output like [this]("http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_2000#Making_it_Work").

I have already tried plugging the card into other PCI slots.  However, it is not even detected by lspci in other slots.  I am wondering if there is something wrong with the motherboard here?  The board is an ASUS P4P800.  Can anyone explain why the driver fails to detect the card, or why lspci fails to list the card in other PCI slots?

---

### Post by xingmu on 2009-03-20
Figured out this problem was due to poor signal between the card and motherboard, i.e. dust.  Cleaned connections with rubbing alcohol and the card was detected fine.  This card is indeed fully supported with the v4l drivers.

---

