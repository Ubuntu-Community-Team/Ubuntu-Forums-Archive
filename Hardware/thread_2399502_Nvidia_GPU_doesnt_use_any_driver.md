---
title: "Nvidia GPU doesnt use any driver"
date: 2018-08-26
forum: Hardware
---

### Post by mistrjirka on 2018-08-26
Hi, I have mx150 and UHD620 in my laptop (Ubuntu 18.04). I am trying to install non-opensource drivers for Nvidia card, and I succesfully installed them, but Nvidia card was still using Nouveau, so I blacklisted Nouveau. Now my nvidia gpu doesnt use any driver. This is my lspci -k ```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
    Subsystem: Lenovo Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
    Subsystem: Lenovo UHD Graphics 620
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
    Subsystem: Lenovo Sunrise Point-LP USB 3.0 xHCI Controller
    Kernel driver in use: xhci_hcd
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
    Subsystem: Lenovo Sunrise Point-LP Thermal subsystem
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
    Subsystem: Lenovo Sunrise Point-LP Serial IO I2C Controller
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
    Subsystem: Lenovo Sunrise Point-LP CSME HECI
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 21)
    Subsystem: Lenovo 82801 Mobile SATA Controller [RAID mode]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
    Subsystem: Lenovo Device 3804
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
    Subsystem: Lenovo Sunrise Point-LP PMC
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: Lenovo Sunrise Point-LP HD Audio
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
    Subsystem: Lenovo Sunrise Point-LP SMBus
    Kernel modules: i2c_i801
01:00.0 3D controller: NVIDIA Corporation GP108M [GeForce MX150] (rev a1)
    Subsystem: Lenovo GP108M [GeForce MX150]
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31)
    Subsystem: Lenovo QCA9377 802.11ac Wireless Network Adapter
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci


``` this is part only with Nvidia ```
01:00.0 3D controller: NVIDIA Corporation GP108M [GeForce MX150] (rev a1)
    Subsystem: Lenovo GP108M [GeForce MX150]
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
```
Why my Nvidia gpu doesnt use any of the Kernel modules like "nvidia, nvidia_drm"?

---

### Post by Bashing-om on 2018-08-26
Hi mistrjirka; Welcome to the forum :)

1st, what diver did you install and from where ?
what shows from terminal commands:
```

dpkg -l | grep -i nvidia
lsmod | grep nvidia

```
see: [https://www.nvidia.com/Download/driverResults.aspx/136120/en-us](https://www.nvidia.com/Download/driverResults.aspx/136120/en-us)
that the 390 version is recommeded.
what does X think ?
```

cat /var/log/Xorg.0.log

```
and what does the GPU manager have to say ?
```

cat /var/log/gpu-manager.log

```

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]we see what we can see
[/INDENT][/INDENT]

---

