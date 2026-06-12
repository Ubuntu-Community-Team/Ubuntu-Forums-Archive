---
title: "Using the Onboard VGA output with a PCIe video card. Both nVidia"
date: 2011-03-12
forum: Hardware
---

### Post by sebikul on 2011-03-12
Hi all!!

I have 2 video cards, one On board, a "nVidia 6150SE nForce 430" and a PCIe "nVidia GeForce GT 220 1GB DDR2 RAM"

I have already configured the PCIe card to use the dual monitor feature, using the VGA and HDMI ports, but now I want to add a third monitor, using the On board VGA port

I have managed to enable the On board graphics processor, which is taking 400MB of ram, but I cant manage to use it, `nvidia-settings` does not detect it, like it's not usable (but is there)


My questions are the following:

1. How can I manage to get the On board VGA display to work together with the PCIe graphics card?

2. If possible, how can I recover those 400 MB the on board card is taking (even without being used) or how can I get it to use the PCIe card available memory?

***
System Details:

```
    Linux 2.6.35-28-generic i686 Ubuntu 10.10 (All updates installed)
    NVIDIA Driver Version: 260.19.06 (Official)
```

If more info is needed please let me know.



Here is the "lspci" output when the On board card is disabled:

	```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
	00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
	00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
	00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
	00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
	00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
	00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
	00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	01:09.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
	02:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
	02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
```


And this is when both are enabled:

	```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
	00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
	00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
	00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
	00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
	00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
	00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
	00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	01:09.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
	02:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
	02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

```

Output of "lshw -class display":

  	 ```
 *-display
	       description: VGA compatible controller
	       product: GT216 [GeForce GT 220]
	       vendor: nVidia Corporation
	       physical id: 0
	       bus info: pci@0000:02:00.0
	       version: a2
	       width: 64 bits
	       clock: 33MHz
	       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
	       configuration: driver=nvidia latency=0
	       resources: irq:18 memory:df000000-dfffffff memory:c0000000-cfffffff memory:da000000-dbffffff ioport:ef80(size=128) memory:def80000-deffffff
	  *-display
	       description: VGA compatible controller
	       product: C61 [GeForce 6150SE nForce 430]
	       vendor: nVidia Corporation
	       physical id: d
	       bus info: pci@0000:00:0d.0
	       version: a2
	       width: 64 bits
	       clock: 66MHz
	       capabilities: pm msi vga_controller bus_master cap_list rom
	       configuration: driver=nvidia latency=0
	       resources: irq:22 memory:dd000000-ddffffff memory:b0000000-bfffffff memory:dc000000-dcffffff memory:deb40000-deb5ffff
```



If what I'm looking for is not possible, please tell me, so I can disable the On board card and recover those 400MB of wasted RAM

Thanks for your help!

---

### Post by gordintoronto on 2011-03-12
I don't have a solution, just a quick comment: the memory on the video card is physically not usable by the on-board video adapter.

I wish you luck. I see frequent complaints about third monitors and few solutions. At least both your adapters are Nvidia, so you might find a solution, if you spend long enough with Google.

---

