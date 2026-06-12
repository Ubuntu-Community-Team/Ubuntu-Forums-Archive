---
title: "***dmesg &amp; hardware***"
date: 2017-05-07
forum: Hardware
---

### Post by shyler-casavant on 2017-05-07
Team, 

Lenovo Yoga 910 - i7-7500U; Ubuntu 16.04.


For the most part the hardware aspect is reliable and trusty. I have seen some small bugs however.
I am seeing small bugs here and there. dmesg output below. 
Any ideas?
```
[    1.109788] intel_pmc_core: probe of 0000:00:1f.2 failed with error -22
[    1.222551] i915 0000:00:02.0: Direct firmware load for i915/kbl_dmc_ver1_01.bin failed with error -2
[  170.003981] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:01:00.0.bin failed with error -2
[  170.003987] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[  170.004292] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
```

lspci output

```
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)
00:08.0 System peripheral: Intel Corporation Sky Lake Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:15.3 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1d.0 PCI bridge: Intel Corporation Device 9d18 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
02:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller (rev 01)
```

---

### Post by ian-weisser on 2017-05-07
Please elaborate - what kind of help do you seek?

Are you asking for an explanation of the output?
Are you asking if those failures are really bugs?
Are you asking how to research and report a bug that you have discovered?
Or something else?

---

### Post by shyler-casavant on 2017-05-07
I'm trying to understand the *** failed with error -2 ***I'm seeing in dmesg and if I should be worried. 
I output the other stuff to see if that could help understand the hardware I have and if anyone had seen this before.

---

### Post by Yellow Pasque on 2017-05-07
```
[  170.003981] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:01:00.0.bin failed with error -2
[  170.003987] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[  170.004292] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
```
From what I can tell, qualcomm/atheros never released the firmware-5.bin file (and may never do so since it's been a couple years since they added the reference to it in the kernel), so it causes those messages. [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/ath10k/QCA6174/hw3.0](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/ath10k/QCA6174/hw3.0)
I wouldn't worry about it, though I agree it is annoying.

```
[    1.109788] intel_pmc_core: probe of 0000:00:1f.2 failed with error -22
[    1.222551] i915 0000:00:02.0: Direct firmware load for i915/kbl_dmc_ver1_01.bin failed with error -2
```

The missing file in question was removed because of this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1645911](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1645911)
Supposedly, it only affected the 4.4 kernel in Ubuntu 16.04.1.  If you're using the 4.8 kernel (the one that Ubuntu 16.04.2), and you care about "additional graphics low-power idle states", maybe you want to try manually installing the file: [https://01.org/linuxgraphics/downloads/kabylake-dmc-1.01](https://01.org/linuxgraphics/downloads/kabylake-dmc-1.01)
If you don't care or don't feel comfortable doing that, don't worry about it.

---

### Post by shyler-casavant on 2017-05-08
Thank you guys so much for letting me know.
I see these errors and think oh no.
Appreciate it.

---

