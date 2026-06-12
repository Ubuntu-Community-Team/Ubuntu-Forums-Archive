---
title: "cannot install latest nvidia driver on 12.10"
date: 2013-03-17
forum: Hardware
---

### Post by Luca Borrione on 2013-03-17
Hello,

I tried to install latest nvidia drivers both on Kubuntu 12.10 and Lubuntu 12.10 without luck.
They both behave the same.

I have an asus s56c ultrabook
```
$ lspci -v00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>


00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915


00:04.0 Signal processing controller: Intel Corporation Device 0153 (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at cfe08000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>


00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, medium devsel, latency 0, IRQ 44
    Memory at f7a00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at f7a22000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei


00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7a20000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd


00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at f7a18000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel


00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f7900000-f79fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f7800000-f78fffff
    Prefetchable memory behind bridge: 00000000f2100000-00000000f21fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7a1f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd


00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich


00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f060 [size=32]
    Memory at f7a1e000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci


00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: medium devsel, IRQ 255
    Memory at f7a1d000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]
    Kernel modules: i2c-i801


00:1f.6 Signal processing controller: Intel Corporation 7 Series/C210 Series Chipset Family Thermal Management Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at f7a1c000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>


01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de3 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb


03:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
    Subsystem: AzureWave Device 1186
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7900000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at f7980000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k


04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7800000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci


04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device 1587
    Flags: bus master, fast devsel, latency 0, IRQ 46
    I/O ports at d000 [size=256]
    Memory at f2104000 (64-bit, prefetchable) [size=4K]
    Memory at f2100000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169



```

I followed this howto [http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html) and did:
```

sudo apt-get install build-essential linux-sourcesudo apt-get install linux-headers-`uname -r`
sudo apt-get install nvidia-current
sudo depmod -a
sudo modprobe nvidia_current

```

and finally I had:
```

$ sudo /sbin/lsmod | grep nvidia 
nvidia              11300876  0

```

Then I rebooted but when I run NVIDIA X server setting I get an alert
> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Now if I run
```
sudo nvidia-xconfig
```

and then reboot I have only 640x480 resolution and I have to manually remove /etc/X11/xorg.conf and reboot.
After that my previous situation is restored.

So: how can I make it working?

I also tried to follow this video tutorial [http://www.youtube.com/watch?v=QtPAJ9BR1W8](http://www.youtube.com/watch?v=QtPAJ9BR1W8) doing:
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade

```

with the very same result as above.

---

### Post by Yellow Pasque on 2013-03-17
You should not install the nvidia driver on a hybrid/Optimus GPU system (the nvidia driver will prevent the Intel graphics from working properly, which is why Additional Drivers doesn't offer it). Instead, remove the nvidia driver:
```
sudo apt-get purge nvidia-current
sudo rm /etc/X11/xorg.conf
```

Then, follow: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Luca Borrione on 2013-03-18
Thank you very much!
Only one more question: I followed the howto you provided but when I run
```
[COLOR=#333333][FONT=monospace]sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic[/FONT][/COLOR]
```

it tries to install lots of 32bit libraries but I installed lubuntu amd64.
I then ran 
```
[COLOR=#333333][FONT=monospace]sudo apt-get install --no-install-recommends bumblebee linux-headers-generic[/FONT][/COLOR]
```

but it seems that it doesn't install any nvidia staff ..

To complete things if I run
```

$ optirun firefox
[  349.860356] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) [drm] failed to open device


[  349.860422] [ERROR]Aborting because fallback start is disabled.



```

---

### Post by Yellow Pasque on 2013-03-19
You need to use the first command if you want to use the nvidia card. It installs 32-bit libs for the nvidia driver in case you want to run 32-bit programs.

---

