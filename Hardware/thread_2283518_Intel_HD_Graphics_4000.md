---
title: "Intel HD Graphics 4000"
date: 2015-06-22
forum: Hardware
---

### Post by akshaygarg-90 on 2015-06-22
Hi I am using ubuntu 14.04 on Lenovo T430s.
Have installed all the latest drivers but the videos on youtube look blurry and pixelated.

As suggested in some forums, have also tried disabling hardware acceleration in flash plugin.

Below components and kernel details :
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
	Subsystem: Lenovo Device [17aa:21fb]
	Kernel driver in use: ivb_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
	Subsystem: Lenovo Device [17aa:21fb]
	Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
	Subsystem: Lenovo Device [17aa:21fb]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
	Subsystem: Lenovo Device [17aa:21fb]
	Kernel driver in use: mei_me
00:16.3 Serial controller [0700]: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller [8086:1e3d] (rev 04)
	Subsystem: Lenovo Device [17aa:21fb]
	Kernel driver in use: serial
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21f3]
	Kernel driver in use: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
	Subsystem: Lenovo Device [17aa:21fb]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
	Subsystem: Lenovo Device [17aa:21fb]
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
	Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
	Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
	Subsystem: Lenovo Device [17aa:21fb]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation QM77 Express Chipset LPC Controller [8086:1e55] (rev 04)
	Subsystem: Lenovo Device [17aa:21fb]
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
	Subsystem: Lenovo Device [17aa:21fb]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
	Subsystem: Lenovo Device [17aa:21fb]
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
	Kernel driver in use: iwlwifi
04:00.0 System peripheral [0880]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 07)
	Subsystem: Lenovo Device [17aa:21fb]
	Kernel driver in use: sdhci-pci


Please suggest what i am doing wrong.

Regards
Akshay

---

### Post by Yellow Pasque on 2015-06-22
Have you tried using html5 in youtube instead of Flash? [https://www.youtube.com/html5](https://www.youtube.com/html5)

---

### Post by weatherman2 on 2015-06-22
Using Firefox or Chrome?  Try both.

---

### Post by akshaygarg-90 on 2015-06-23
Yeah Actually HTML 5 was worse so i had to disable the html 5 and installed flash plugin for chromium.
Firefox also has same issue.

I today downloaded a HD video which seems to be working fine, so i guess the problem is not atleast with the graphics kernel.

I think it should be something with the current flash plugin.

Thoughts !!

---

### Post by akshaygarg-90 on 2015-06-23
I just removed the kernel and re installed it.. working now.
Thanks for the help :)

---

