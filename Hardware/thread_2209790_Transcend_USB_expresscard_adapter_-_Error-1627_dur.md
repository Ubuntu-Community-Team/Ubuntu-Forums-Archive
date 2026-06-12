---
title: "Transcend USB expresscard adapter - Error-1627 during driver installation using wine"
date: 2014-03-07
forum: Hardware
---

### Post by harry18 on 2014-03-07
'm trying to install a USB ExpressCard Adapter on ubuntu - Ts-PNU3 (Transcend)  I have installed Wine and downloaded the relevant driver from the adapters online support downloads.
  when running the setup.exe with wine, I experience error 1627 - Function Failed. And consequently the installation finishes:
  ```
harry@harry-Studio-XPS-1340:~$ wine /home/harry/Desktop/RENESAS-USB3-Host-Driver-21390-Setup-x86-x64-Binary/setup.exe 
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:apphelp:ApphelpCheckInstallShieldPackage stub: 0x32d5fc L"Z:\\home\\harry\\Downloads\\RENESAS-USB3-Host-Driver-21390-Setup-x86-x64-Binary\\nusb3drv.msi"
fixme:ieframe:taskbar_list_SetProgressState iface 0xd01cd8, hwnd 0x20028, flags 2 stub!
fixme:ieframe:taskbar_list_SetProgressValue iface 0xd01cd8, hwnd 0x20028, ullCompleted 0, ullTotal 64 stub!
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2800-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2800-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2800-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2800-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2800-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108

```  Here is the lspci -v output:```


      harry@harry-Studio-XPS-1340:~$ lspci -v
00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
    Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b2)
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 1c00 [size=256]

00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Dell Device 0271
    Flags: 66MHz, fast devsel

00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
    Subsystem: Dell Device 0271
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at 3080 [size=64]
    I/O ports at 3040 [size=64]
    I/O ports at 2000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Dell Device 0271
    Flags: 66MHz, fast devsel

00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at f0600000 (32-bit, non-prefetchable) [size=512K]

00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    Memory at f0686000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at f0689000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:06.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f0687000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:06.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at f0689400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
    Memory at f0680000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    Memory behind bridge: f0300000-f03fffff
    Capabilities: <access denied>

00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at f0688000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 30d0 [size=8]
    Memory at f0689c00 (32-bit, non-prefetchable) [size=256]
    Memory at f0689800 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0b.0 SATA controller: NVIDIA Corporation MCP79 AHCI Controller (rev b1) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 43
    I/O ports at 30e8 [size=8]
    I/O ports at 30dc [size=4]
    I/O ports at 30e0 [size=8]
    I/O ports at 30d8 [size=4]
    I/O ports at 30c0 [size=16]
    Memory at f0684000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:0c.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: ae000000-afefffff
    Prefetchable memory behind bridge: 00000000ce000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: ac000000-acffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000cbffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    Memory behind bridge: f0000000-f01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Memory behind bridge: f0200000-f02fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:17.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:18.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

01:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
    Subsystem: Dell Device 0271
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f0300000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

01:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Subsystem: Dell Device 0271
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f0300800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

01:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Dell Device 0271
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f0301000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r592
    Kernel modules: r592

01:07.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
    Subsystem: Dell Device 0271
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f0301400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r852
    Kernel modules: r852

02:00.0 VGA compatible controller: NVIDIA Corporation GT218M [GeForce G210M] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0271
    Flags: fast devsel, IRQ 23
    Memory at ae000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ce000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 4000 [size=128]
    Expansion ROM at af000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel modules: nouveau, nvidiafb

03:00.0 VGA compatible controller: NVIDIA Corporation C79 [GeForce 9400M G] (rev b1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0271
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at ac000000 (32-bit, non-prefetchable) [size=16M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at ca000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 5000 [size=128]
    [virtual] Expansion ROM at c0000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
    Flags: fast devsel, IRQ 22
    Memory at f0000000 (64-bit, non-prefetchable) [disabled] [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

06:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Dell Wireless 1510 Wireless-N WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

```  Any help would be greatly appreciated!!

---

### Post by Mark Phelps on 2014-03-07
You can't install Windows drivers using Wine -- that's not what it does.  And, even if you could, they would NOT work, as you need Linux drivers, not Windows drifers.

---

### Post by harry18 on 2014-03-07
> **Mark Phelps said:**
> You can't install Windows drivers using Wine -- that's not what it does.  And, even if you could, they would NOT work, as you need Linux drivers, not Windows drifers.

So is there readily available Linux drivers for this particular product or do I need to purchase a specifically Linux capable adapter?

If so can you recommend any?

---

