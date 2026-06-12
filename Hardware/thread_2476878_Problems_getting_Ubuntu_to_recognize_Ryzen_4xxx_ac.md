---
title: "Problems getting Ubuntu to recognize Ryzen 4xxx accelerometer sensor"
date: 2022-07-10
forum: Hardware
---

### Post by radumarinoiu98 on 2022-07-10
Hi everyone!

[SIZE=4] Let me start with my setup:[/SIZE]
Software: Ubuntu 22.04 running Gnome 42.2 using Wayland on Kernel 5.15.0-40-generic
Hardware: ASUS VivoBook Flip 14 TM420IA, Ryzen 4500U with Radeon Graphics (It's a 2in1)

[SIZE=4] The Problem:[/SIZE]
No matter what I try, I cannot get the screen to rotate when rotating the device.

[SIZE=4] Findings so far:[/SIZE]
I've tried searching for someone in the same boat as I am, without success, for 2 days straight. I decided it was about time I posted my own question, maybe someone can help me debug the issue or tell me to leave it dead cuz I can't do anything about it.
I've discovered people with similar hardware (Ryzen Renoir) that have the same Sensor Fusion Hub model as I do, that have their sensors detected, albeit with other problems, but this indicates to me that drivers included in Linux 5.15 should work with Renoir SFH. (see: [https://bugzilla.kernel.org/show_bug.cgi?id=207431](https://bugzilla.kernel.org/show_bug.cgi?id=207431))
I also found people making their Ryzen 3xxx work with older kernels (5.11-5.12 I think), but Renoir still didn't work using those kernels, as it's a different architecture from Ryzen 3xxx.

[SIZE=4] Debugging:[/SIZE]
** lspci -knn**
```
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne Root Complex [1022:1630]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne Root Complex [1022:1630]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne IOMMU [1022:1631]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne IOMMU [1022:1631]
00:01.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge [1022:1632]
00:01.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge [1022:1634]
    Kernel driver in use: pcieport
00:01.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge [1022:1634]
    Kernel driver in use: pcieport
00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge [1022:1632]
00:08.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge [1022:1632]
00:08.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus [1022:1635]
    Kernel driver in use: pcieport
00:08.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus [1022:1635]
    Kernel driver in use: pcieport
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:790b] (rev 51)
    Subsystem: ASUSTeK Computer Inc. FCH SMBus Controller [1043:11f2]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:790e] (rev 51)
    Subsystem: ASUSTeK Computer Inc. FCH LPC Bridge [1043:11f2]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 0 [1022:1448]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 1 [1022:1449]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 2 [1022:144a]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 3 [1022:144b]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 4 [1022:144c]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 5 [1022:144d]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 6 [1022:144e]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 7 [1022:144f]
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8822CE 802.11ac PCIe Wireless Network Adapter [10ec:c822]
    Subsystem: Lite-On Communications Inc RTL8822CE 802.11ac PCIe Wireless Network Adapter [11ad:0810]
    Kernel driver in use: rtw_8822ce
    Kernel modules: rtw88_8822ce
02:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller 980 [144d:a809]
    DeviceName: Onboard LAN Brodcom
    Subsystem: Samsung Electronics Co Ltd Device [144d:a801]
    Kernel driver in use: nvme
    Kernel modules: nvme
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Renoir [1002:1636] (rev c3)
    Subsystem: ASUSTeK Computer Inc. Renoir [1043:11f2]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu
03:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Renoir Radeon High Definition Audio Controller [1002:1637]
    Subsystem: ASUSTeK Computer Inc. Renoir Radeon High Definition Audio Controller [1043:11f2]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
03:00.2 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor [1022:15df]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor [1022:15df]
    Kernel driver in use: ccp
    Kernel modules: ccp
03:00.3 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne USB 3.1 [1022:1639]
    Subsystem: ASUSTeK Computer Inc. Renoir/Cezanne USB 3.1 [1043:201f]
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci
03:00.4 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne USB 3.1 [1022:1639]
    Subsystem: ASUSTeK Computer Inc. Renoir/Cezanne USB 3.1 [1043:201f]
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci
03:00.5 Multimedia controller [0480]: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor [1022:15e2] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Raven/Raven2/FireFlight/Renoir Audio Processor [1043:11f2]
    Kernel modules: snd_pci_acp3x, snd_rn_pci_acp3x, snd_pci_acp5x
03:00.6 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller [1022:15e3]
    DeviceName: HD Audio Controller
    Subsystem: ASUSTeK Computer Inc. Family 17h (Models 10h-1fh) HD Audio Controller [1043:1d4e]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
03:00.7 Signal processing controller [1180]: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/Renoir Sensor Fusion Hub [1022:15e4]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/Renoir Sensor Fusion Hub [1022:15e4]
    Kernel driver in use: pcie_mp2_amd
    Kernel modules: amd_sfh
04:00.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901] (rev 81)
    Subsystem: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901]
    Kernel driver in use: ahci
    Kernel modules: ahci
04:00.1 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901] (rev 81)
    Subsystem: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901]
    Kernel driver in use: ahci
    Kernel modules: ahci
```

**udevadm info --export-db | grep -I iio** - No Output

** lsmod | grep amd**
```
edac_mce_amd           36864  0
kvm_amd               151552  0
kvm                  1003520  1 kvm_amd
ccp                   102400  1 kvm_amd
amd_pmc                20480  0
amdgpu               9723904  32
iommu_v2               24576  1 amdgpu
gpu_sched              45056  1 amdgpu
i2c_algo_bit           16384  1 amdgpu
drm_ttm_helper         16384  1 amdgpu
ttm                    86016  2 amdgpu,drm_ttm_helper
drm_kms_helper        307200  1 amdgpu
drm                   606208  17 gpu_sched,drm_kms_helper,amdgpu,drm_ttm_helper,ttm
amd_sfh                36864  0
hid                   147456  4 i2c_hid,hid_multitouch,hid_generic,amd_sfh
```

**ls /sys/bus/iio/devices/** - No Output

**ls /sys/bus/hid/devices**
```
0018:04F3:2BC8.0002  0018:04F3:3115.0001
```

**monitor-sensor**
```
Waiting for iio-sensor-proxy to appear
```

**G_MESSAGES_DEBUG=all /usr/libexec/iio-sensor-proxy** (as root)
```
** (iio-sensor-proxy:61748): DEBUG: 20:23:49.969: No sensors or missing kernel drivers for the sensors
```

[SIZE=4] Conclusions:[/SIZE]
I am not an expert in low level interactions between device buses and how kernels work, etc. but I do have background in CS and I understand some of those things or at least I think so...
It seems to me like the drivers for the SFH are installed and loaded in the Kernel, and the drivers for 5.15 should correctly identify sensors for my Hardware. I also understand that iio-sensor-proxy cannot be expected to run when there is no IIO sensor device available, and as such my conclusion is that the problem is with the drivers that do not work for my sensors.

Could somebody help me diagnose this further?
Thanks a lot for taking the time to read this, and let me know what other info I could provide to help diagnose this issue.

---

### Post by ruufus on 2022-08-30
Hello,
i got the exact same Problem on an HP Envy with AMD 4700 CPU.
Does anyone got a Solution or something I can try out?
Thanks!

---

### Post by t3do on 2023-05-15
Hi,
I have exactly the same problem like radumarinoiu98 with the same system setting (2in1 Laptop, which is the Asus Vivobook Flip 14 TM420).
Can anyone help us please? I am searching for days and can not find a solution
Thanks in advance ;-)

---

