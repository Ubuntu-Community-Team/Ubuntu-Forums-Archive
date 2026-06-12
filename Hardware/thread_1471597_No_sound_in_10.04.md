---
title: "No sound in 10.04"
date: 2010-05-03
forum: Hardware
---

### Post by Zolaboony on 2010-05-03
Hello, I know that there is a lot of posts about sound not working but after looking at them I still cant fix my problem. 

I think my sound card is not being picked up because:

```
tom@ubuntu:~$ aplay -l
aplay: device_list:223: no soundcards found...

``` 

But when I type in lspci -v:

```
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
	Subsystem: Acer Incorporated [ALI] Device 0157
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

So it finds the actual hardware but it isnt working correctly, if the driver is causing the problem, where could I download one from my sound card?

Thanks

---

