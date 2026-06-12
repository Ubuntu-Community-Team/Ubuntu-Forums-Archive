---
title: "No Sound on Intel NUC kit DN2820FYKH"
date: 2014-02-22
forum: Hardware
---

### Post by kindrudekid on 2014-02-22
So I bought this Kit to get XBMC working, I am gonna switch to OpenElec when the stable comes out but for now I would like to keep using Ubuntu + XBMC.

As per recommendation, last week I installed the daily ppa for pulse audio and tonight I did a dist-upgrade which gave me a new kernel and this killed sound on my ubuntu.

I cannot open the device chooser and I already purged the previous kernels.


**output 1:**

```
    xbmc@xbmc09t67-./9~$ aplay -l
    aplay: device_list:268: no soundcards found...
```


**Outout 2:**

```
    xbmc@xbmc:~$ sudo modprobe snd-hda-intel
    ERROR: could not insert 'snd_hda_intel': Unknown symbol in module, or unknown parameter (see dmesg)

```

**Output 3:**
```

    xbmc@xbmc:~$ lspci -v
    00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0c)
    	Subsystem: Intel Corporation Device 2055
    	Flags: bus master, fast devsel, latency 0
    
    00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0c) (prog-if 00 [VGA controller])
    	Subsystem: Intel Corporation Device 2055
    	Flags: bus master, fast devsel, latency 0, IRQ 106
    	Memory at d0000000 (32-bit, non-prefetchable) [size=4M]
    	Memory at c0000000 (32-bit, prefetchable) [size=256M]
    	I/O ports at f080 [size=8]
    	Expansion ROM at <unassigned> [disabled]
    	Capabilities: <access denied>
    	Kernel driver in use: i915
    
    00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0c) (prog-if 01 [AHCI 1.0])
    	Subsystem: Intel Corporation Device 2055
    	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 104
    	I/O ports at f070 [size=8]
    	I/O ports at f060 [size=4]
    	I/O ports at f050 [size=8]
    	I/O ports at f040 [size=4]
    	I/O ports at f020 [size=32]
    	Memory at d0816000 (32-bit, non-prefetchable) [size=2K]
    	Capabilities: <access denied>
    	Kernel driver in use: ahci
    
    00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0c) (prog-if 30 [XHCI])
    	Subsystem: Intel Corporation Device 2055
    	Flags: bus master, medium devsel, latency 0, IRQ 103
    	Memory at d0800000 (64-bit, non-prefetchable) [size=64K]
    	Capabilities: <access denied>
    	Kernel driver in use: xhci_hcd
    
    00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0c)
    	Subsystem: Intel Corporation Device 2055
    	Flags: bus master, fast devsel, latency 0, IRQ 255
    	Memory at d0500000 (32-bit, non-prefetchable) [size=1M]
    	Memory at d0400000 (32-bit, non-prefetchable) [size=1M]
    	Capabilities: <access denied>
    
    00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0c)
    	Subsystem: Intel Corporation Device 2055
    	Flags: bus master, fast devsel, latency 0, IRQ 4
    	Memory at d0810000 (64-bit, non-prefetchable) [size=16K]
    	Capabilities: <access denied>
    
    00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
    	Flags: bus master, fast devsel, latency 0
    	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    	I/O behind bridge: 00002000-00002fff
    	Capabilities: <access denied>
    	Kernel driver in use: pcieport
    
    00:1c.1 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
    	Flags: bus master, fast devsel, latency 0
    	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    	I/O behind bridge: 00003000-00003fff
    	Memory behind bridge: d0700000-d07fffff
    	Capabilities: <access denied>
    	Kernel driver in use: pcieport
    
    00:1c.2 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
    	Flags: bus master, fast devsel, latency 0
    	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    	I/O behind bridge: 0000e000-0000efff
    	Memory behind bridge: d0600000-d06fffff
    	Capabilities: <access denied>
    	Kernel driver in use: pcieport
    
    00:1c.3 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
    	Flags: bus master, fast devsel, latency 0
    	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    	I/O behind bridge: 00004000-00004fff
    	Capabilities: <access denied>
    	Kernel driver in use: pcieport
    
    00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0c)
    	Subsystem: Intel Corporation Device 2055
    	Flags: bus master, medium devsel, latency 0
    	Capabilities: <access denied>
    
    00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0c)
    	Subsystem: Intel Corporation Device 2055
    	Flags: medium devsel, IRQ 5
    	Memory at d0814000 (32-bit, non-prefetchable) [size=32]
    	I/O ports at f000 [size=32]
    	Capabilities: <access denied>
    
    02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
    	Subsystem: Intel Corporation Wireless-N 7260
    	Flags: bus master, fast devsel, latency 0, IRQ 107
    	Memory at d0700000 (64-bit, non-prefetchable) [size=8K]
    	Capabilities: <access denied>
    	Kernel driver in use: iwlwifi
    
    03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
    	Subsystem: Intel Corporation Device 2055
    	Flags: bus master, fast devsel, latency 0, IRQ 105
    	I/O ports at e000 [size=256]
    	Memory at d0604000 (64-bit, non-prefetchable) [size=4K]
    	Memory at d0600000 (64-bit, prefetchable) [size=16K]
    	Capabilities: <access denied>
    	Kernel driver in use: r8169
```

---

