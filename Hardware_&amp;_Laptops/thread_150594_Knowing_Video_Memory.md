---
title: "Knowing Video Memory"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by alvonsius on 2006-03-26
Hi all, is there any way to find out how much my video RAM is? I'm using Intel i915 on-board now. Here are some information I can provide to you:

BIOS tell me that the maximum share memory is 128MB for the VGA

From the dmesg | grep agp I get 
agpgart: Detected 7932K stolen memory.

And in the xorg.conf I have written
VideoRam        64000

And still I can't convice myself that I'm using 64MB VGA ](*,) . Is there any way to know it? And if somehow I'm still using 8MB RAM(as the kernel give to me), is there any way I can rise it to 64MB?

TIA ...

---

### Post by Ensnared on 2006-03-26
I don't have an onboard card that shares memory with the system that way, but the RAM in my board is listed if I execute "lspci -v" - try that and see what it says.

For reference, here's the output for the relevant device for my box (the line with the video RAM is marked red):
```
0000:03:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc: Unknown device 0002
        Flags: bus master, stepping, 66MHz, medium devsel, latency 255, IRQ 19
[color=red]        Memory at d0000000 (32-bit, prefetchable) [size=128M][/color]
        I/O ports at d000 [size=256]
        Memory at e3000000 (32-bit, non-prefetchable) [size=64K]

```

---

