---
title: "Intel i7-8565U CPU - device is not working - drivers, running ubuntu 18.04"
date: 2022-06-10
forum: Hardware
---

### Post by c2wbob on 2022-06-10
Hey so it's my first post ever here, recently installed ubuntu 18.04 on an external SSD.
 
I can't seem to find any drivers for my CPU and find it weird it says device not working in the drivers menu.

Here is a screenshot and some data I can provide:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290592&stc=1[/IMG]
I ran the following commands:
  ```
cat /proc/cpuinfo | grep 'name' | uniq
```
result:
```
model name    : Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz
```
and ```
lspci -nnk
```
result:
```
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:3e34] (rev 0b)    Subsystem: ASUSTeK Computer Inc. Device [1043:14a1]
    Kernel driver in use: skl_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:3ea0]
    Subsystem: ASUSTeK Computer Inc. Device [1043:14a1]
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller [1180]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [8086:1903] (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [1043:14a1]
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device
00:08.0 System peripheral [0880]: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model [8086:1911]
    Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model [1043:14a1]
00:12.0 Signal processing controller [1180]: Intel Corporation Device [8086:9df9] (rev 30)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14a1]
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal
00:14.0 USB controller [0c03]: Intel Corporation Device [8086:9ded] (rev 30)
    Subsystem: ASUSTeK Computer Inc. Device [1043:201f]
    Kernel driver in use: xhci_hcd
00:14.2 RAM memory [0500]: Intel Corporation Device [8086:9def] (rev 30)
    Subsystem: Intel Corporation Device [8086:7270]
00:14.3 Network controller [0280]: Intel Corporation Device [8086:9df0] (rev 30)
    Subsystem: Intel Corporation Device [8086:0034]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
00:14.5 SD Host controller [0805]: Intel Corporation Device [8086:9df5] (rev 30)
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci
00:15.0 Serial bus controller [0c80]: Intel Corporation Device [8086:9de8] (rev 30)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14a1]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:15.1 Serial bus controller [0c80]: Intel Corporation Device [8086:9de9] (rev 30)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14a1]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:15.3 Serial bus controller [0c80]: Intel Corporation Device [8086:9deb] (rev 30)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14a1]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:16.0 Communication controller [0780]: Intel Corporation Device [8086:9de0] (rev 30)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14a1]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:19.0 Serial bus controller [0c80]: Intel Corporation Device [8086:9dc5] (rev 30)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14a1]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:9db8] (rev f0)
    Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation Device [8086:9dbc] (rev f0)
    Kernel driver in use: pcieport
00:1d.0 PCI bridge [0604]: Intel Corporation Device [8086:9db4] (rev f0)
    Kernel driver in use: pcieport
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:9d84] (rev 30)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14a1]
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:9dc8] (rev 30)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14a1]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci
00:1f.4 SMBus [0c05]: Intel Corporation Device [8086:9da3] (rev 30)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14a1]
    Kernel modules: i2c_i801
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device [8086:9da4] (rev 30)
    Subsystem: Intel Corporation Device [8086:7270]
02:00.0 3D controller [0302]: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] [10de:1c8d] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GP107M [GeForce GTX 1050 Mobile] [1043:14a1]
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
03:00.0 Non-Volatile memory controller [0108]: Sandisk Corp Device [15b7:5003] (rev 01)
    Subsystem: Sandisk Corp Device [15b7:5003]
    Kernel driver in use: nvme
    Kernel modules: nvme

```

From what I can tell intel doesn't have any drivers for this CPU for linux, any alternatives? And should I worry about the 'device not working'?

---

### Post by tea for one on 2022-06-10
Just a bit of clarification required.
The screenshot and text info were supplied via a live session (i.e. Try Ubuntu) or from your Ubuntu installation on the external ssd?

---

### Post by mikewhatever on 2022-06-10
It is unclear why you think that CPU "is not working" or why you need "drivers for my CPU" and how many drivers, all that while "running ubuntu 18.04".
Is there another CPU with drivers that does the job?

---

### Post by Yellow Pasque on 2022-06-11
Your screenshot shows the Ubuntu drivers utility complaining about the wireless chip (not the CPU). If your wireless is working or you're not using it, don't worry about it.
Also, you can run this to update the PCI ID database. Instead of saying "Intel Corp.: Unknown" it should specify the name of the device.
```
sudo update-pciids
```

---

### Post by c2wbob on 2022-06-11
Alrighty thanks for this clarification, the command didn't fix it I just thought there were some driver I needed

---

### Post by c2wbob on 2022-06-11
It's running from an ubuntu installation on the ssd, not the right version.I thought I needed some driver but it seems not

---

### Post by Yellow Pasque on 2022-06-11
> **c2wbob said:**
> the command didn't fix it

The command wasn't supposed to fix it. All 'update-pciids' does is update the names of PCI devices so lspci is more informative on older systems.

So again, are you using wireless and is it working?

---

### Post by c2wbob on 2022-06-12
yes I am using it and it it is working.. so there's nothing to worry about

---

