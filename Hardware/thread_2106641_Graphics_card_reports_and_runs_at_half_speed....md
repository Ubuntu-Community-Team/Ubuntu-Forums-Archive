---
title: "Graphics card reports and runs at half speed...?"
date: 2013-01-19
forum: Hardware
---

### Post by robert shearer on 2013-01-19
I run, by neccessity, some old hardware (AMD K8 '3000+', 2 Gig of Ram, and Radeon 9550 128 MB Graphics,  all circa 2005)
Yesterday at a thrift store I picked up an old Dell dimension 8200 that had been 'pimped out' with a Sapphire Radeon HD 3650 card.
This is the **AGP version**, 8xAGP,512 MB, DDR2, from about 2008.

I swapped it into the K8 setup (above) and graphics performance has improved but not as much as I had hoped for.

On checking with sudo lshw and lspci -v -s I find that although the card is reported by model correctly the memory is only shown as 256 MB (half the 512 MB it should be.)
In Windows it also works but is shown as a series lower (AMD 2xxx instead of AMD 3650)

I am guessing here but as the reports are exactly **half** of what the card is then the problem is using a card having DDR2 memory in a board running DDR....?  and if this is correct then so be it and I will be happy with the small performance gain that brings.
**Edit...** Researched and so the fact it is DDR2 should not be an issue and it should report and run as 512MB.

As I am not interested in gaming or video editing but photo editing then perhaps this will suffice.

However, I see in Bios that there is an option...
'AGP Overclock in MHz'  that is currently at the lowest (normal ?) setting of 66 but runs up in steps of 1 increment all the way to 100.

Thus my question is will changing this improve performance and what can anyone recommend I set it to...?

Any other suggestions...?

output from lshw and lspci....
```
sudo lshw
*-display
                description: VGA compatible controller
                product: RV635 PRO AGP [Radeon HD 3650]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:d0000000-dfffffff ioport:a000(size=[COLOR="Red"]256[/COLOR]) memory:e9000000-e900ffff memory:e8000000-e801ffff


sudo lspci -v -s 01:00.0
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV635 PRO AGP [Radeon HD 3650] (prog-if 00 [VGA controller])
	Subsystem: Hightech Information System Ltd. Device 0028
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=[COLOR="Red"]256M[/COLOR]
	I/O ports at a000 [size=256]
	Memory at e9000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at e8000000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] AGP version 3.0
	Kernel driver in use: radeon
	Kernel modules: radeon

```

**Edit....** more research and it seems that lshw and lspci have limits to the values they return (they lie :-) )
so 
```
dmesg | grep VRAM
```
 returns...
[   11.707179] radeon 0000:01:00.0: VRAM: 512M 0xC0000000 - 0xDFFFFFFF ([COLOR="Red"]512M[/COLOR] used)
[   11.707663] [drm] Detected VRAM RAM=[COLOR="Red"]512M[/COLOR], BAR=256M
[   11.712164] [drm] radeon: [COLOR="Red"]512M[/COLOR] of VRAM memory ready

That solves it for Ubuntu, now off to sort the Windows error...maybe driver ??
oh well, strange how coincidences conspire to lead us astray... :o

Cheers,
Bob

---

