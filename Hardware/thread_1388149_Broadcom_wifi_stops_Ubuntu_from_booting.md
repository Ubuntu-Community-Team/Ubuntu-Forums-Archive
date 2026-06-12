---
title: "Broadcom wifi stops Ubuntu from booting"
date: 2010-01-22
forum: Hardware
---

### Post by Znupi on 2010-01-22
**I'm not sure where to post this, as I have already found a solution. I'm merely posting it to help others who might be in the same situation.**

I just got a new laptop (a HP ProBook 4515s, if that helps) which has a Broadcom wifi card:
```
$ lspci | grep -i broadcom
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```
Obviously, I tried installing Ubuntu on this machine. Unfortunately, after installing Ubuntu 9.10, it would have trouble booting -- sometimes it would boot just fine, sometimes it would just hang after GRUB, before the white glowing Ubuntu logo is supposed to appear. I thought applying the latest updates would help but they didn't seem to, they actually made booting worse (it would fail more often than before).

At this point I thought maybe something went wrong with the Ubuntu installation and reinstalled it, but got the same issues.

So, the second time, after applying all updates I struggled to get it to boot -- finally I was able to boot into single user mode by modifying the commands in GRUB, but even so I had to try a few times for it to work. What ultimately fixed it was **installing the restricted wifi drivers** (sudo jockey-text -e kmod:wl). This seemed like a long shot but I was pretty desperate. Incredibly, the machine works perfectly fine after installing these drivers.

I don't know what caused this problem (I'm guessing some faulty kernel modules -- or good, open source modules conflicting with proprietary hardware), I don't know if I should report this bug and where (since it's pretty severe), I just know that I've gone through a lot of headaches to get it to work and maybe I can help someone else having the same problems.

For anyone with this problem: it might help turning off WLAN from the BIOS when trying to boot with the faulty drivers, installing the proprietary ones and then re-enabling WLAN. I didn't try this myself because I didn't know what the problem was.

---

### Post by efflandt on 2010-01-23
I don't think your issue had anything to do with the BCM4312, unless something else was conflicting with it.  I recently installed 64-bit Ubuntu 9.10 on a Dell 1545 with same wireless device and the only issue I had might have been because I was using a supported USB wireless device when I went to Hardware Drivers to activate "Broadcom STA".  After activation it hung searching for other drivers and I could not close it.  Maybe it got confused with 2 different types of wireless connected at the same time.  But after rebooting without the USB wireless, the BCM4312 worked fine.

Alternately if you have no network connection at all, it is possible to install bcmwl-kernel-source from the installation CD by adding it to Synaptic.

---

### Post by Znupi on 2010-01-23
I didn't have anything connected to the machine, not even a mouse. And since it worked perfectly the moment I installed those drivers, I don't see what else it could be. The only thing that crosses my mind is bluetooth -- maybe the Broadcom STA drivers also contain drivers for bluetooth. Still, this wouldn't fit the fact that Ubuntu seemed to recognize the bluetooth (the bluetooth icon appeared in the tray, I did not try to pair it with any device or anything). Here's my entire lspci, maybe it helps determine the exact problem:
```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 10)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```
Also, maybe you don't have the exact same BCM4312, maybe your revision number is different, maybe it's not 802.11b/g but a/b/g.
**Edit:** here's my lsusb, too:
```
$ lsusb 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

