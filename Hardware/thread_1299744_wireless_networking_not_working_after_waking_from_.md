---
title: "wireless networking not working after waking from ram suspend"
date: 2009-10-24
forum: Hardware
---

### Post by edke on 2009-10-24
Hello guys.

I'm having problems with RAM suspend and restoring wireless networking after waking up since I brought my notebook. It's Asus X50Z.

It didn't work on Jaunty and now after upgrading to Karmic betas and rc issue still persists. I used NetworkManager, after so many issues with it I switched to wicd which just works great, but still no wireless after suspend.

This is my lspci, if any more info needed, I'll gladly provide.

```




00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
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
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

---

### Post by ronocdh on 2009-11-10
Any luck? I'm in the process of researching this, too. I'll post back here if I do find anything of value.

---

### Post by edke on 2009-11-11
> **ronocdh said:**
> Any luck? I'm in the process of researching this, too. I'll post back here if I do find anything of value.

No, didn't resolve it yet :(

---

### Post by antonpiatek on 2009-11-11
Have you looked at the end of the output from dmesg after resuming from suspend?
I had some issues occasionally where my wireless driver could not reload during resume.
my driver is ipw2200, so a "sudo rmmod ipw2200; modprobe ipw2200" reloaded the driver and caused it to work

---

### Post by ronocdh on 2009-11-11
> **antonpiatek said:**
> Have you looked at the end of the output from dmesg after resuming from suspend?
I had some issues occasionally where my wireless driver could not reload during resume.
my driver is ipw2200, so a "sudo rmmod ipw2200; modprobe ipw2200" reloaded the driver and caused it to work
Thank you, I'll try that.

What I did find was [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/275692") that recommends adding "ath_pci" to a list of exceptions for suspend. It did *not* work for me, not even after making the change and restarting, then trying to respond.

---

### Post by edke on 2009-11-17
I had a little time to play with this issue today and found out that after modproble -r ath9k and modprobe ath9k my wireless worked when ifconfig wlan0 up was issued. So I searched a bit again and found solution that is working for me:

[http://ubuntuforums.org/showpost.php?p=6426626&postcount=4](http://ubuntuforums.org/showpost.php?p=6426626&postcount=4)


It even works after multiple suspends. Hope that it helps.

---

