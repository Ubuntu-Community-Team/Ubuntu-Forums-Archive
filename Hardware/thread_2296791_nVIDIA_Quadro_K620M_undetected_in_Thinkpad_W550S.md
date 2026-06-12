---
title: "nVIDIA Quadro K620M undetected in Thinkpad W550S"
date: 2015-09-28
forum: Hardware
---

### Post by codonnel on 2015-09-28
I'm on Ubuntu 15.04, and my graphics card isn't getting detected by ubuntu-drivers. I tried installing the latest nvidia drivers (apt-get install nvidia-346) in the hope that would help detect the graphics card, but it made no difference. Below is the output of the commands I thought might be relevant. Of course, I'm happy to furnish further info.

```
lspci -v

00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)    Subsystem: Lenovo Device 2223
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>


00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 2225
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915


00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
    Subsystem: Lenovo Device 2223
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at f2230000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel


00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 2223
    Flags: bus master, medium devsel, latency 0, IRQ 40
    Memory at f2220000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
    Subsystem: Lenovo Device 2223
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f2239000 (64-bit, non-prefetchable) [size=32]
    Capabilities: <access denied>
    Kernel driver in use: mei_me


00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (3) I218-V (rev 03)
    Subsystem: Lenovo Device 2226
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f2200000 (32-bit, non-prefetchable) [size=128K]
    Memory at f223e000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 4080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e


00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
    Subsystem: Lenovo Device 2223
    Flags: bus master, fast devsel, latency 32, IRQ 47
    Memory at f2234000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #6 (rev e3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: f2100000-f21fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1c.1 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f2000000-f20fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f1000000-f1ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 2223
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f223d000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
    Subsystem: Lenovo Device 2223
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich


00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 2223
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at 40a8 [size=8]
    I/O ports at 40b4 [size=4]
    I/O ports at 40a0 [size=8]
    I/O ports at 40b0 [size=4]
    I/O ports at 4060 [size=32]
    Memory at f223c000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci


00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
    Subsystem: Lenovo Device 2223
    Flags: medium devsel, IRQ 10
    Memory at f2238000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]


00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
    Subsystem: Lenovo Device 2223
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f223b000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>


02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
    Subsystem: Lenovo Device 2223
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f2100000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci


03:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f2000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi


08:00.0 3D controller: NVIDIA Corporation Device 137a (rev a2)
    Subsystem: Lenovo Device 2225
    Flags: fast devsel, IRQ 16
    Memory at f1000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>

```

```
ubuntu-drivers list

intel-microcode
```

```
ubuntu-drivers devices

== cpu-microcode.py ==
driver   : intel-microcode - distro non-free

```

---

### Post by dino99 on 2015-09-29
i does not know about your card model, but 346 is not the latest driver: try 352 or 355 to get better chance
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=vivid](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=vivid)

---

### Post by codonnel on 2015-09-29
I purged all nvidia stuff and installed 355 from the grahpics-drivers PPA, but still no difference. It seems like ubuntu doesn't even recognize the K620M as a video card. It's just not listed in ubuntu-drivers or the GUI additional drivers tab. Any further suggestions?

Edit: I installed bumblebee and altered /etc/bumblebee/bumblebee.conf to reflect that I'm using the nvidia-355 drivers, changing the [driver-nvidia] section as follows (and additionally setting Driver=nvidia to avoid nouveau):

```

Driver=nvidia
...
## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-355
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-355:/usr/lib32/nvidia-355
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-355/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

```

When I run optirun glxheads, it shows that it is using my nvidia card:
```

optirun glxheads                                                                   &#11138; ruby-2.2.1 
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0
  Display:     0x2181b70
  Window:      0x4a00002
  Context:     0x2f9b780
  GL_VERSION:  4.5.0 NVIDIA 355.11
  GL_VENDOR:   NVIDIA Corporation
  GL_RENDERER: Quadro K620M/PCIe/SSE2

```

I guess this is somewhat solved, though ubuntu-drivers still doesn't believe my nvidia card exists. It would be nice, but isn't essential to figure that out.

---

