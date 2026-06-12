---
title: "ThinkPad Edge 11 internal Microphone problem"
date: 2011-01-08
forum: Hardware
---

### Post by ideamaestro on 2011-01-08
Hello Everybody,

I bought my ThinkPad Edge 11" AMD Dual Core in Dec 2010. Googled and solved the Wireless and other driver problems. Now the only trouble I have is the Microphone and head phones. I tried lots of stuff like:

1) adding:
options snd-hda-intel model=ideapad
options snd-hda-intel position_fix=1

in the /etc/modprobe.d/alsa-base.conf  file. changed ideapad to thinkpad, ox..._15 and other values, but nothing works. 

2) Installed, pavcontrol and gnome-alsa mixer and changed values there as well. One tutorial indicated that the mic is a mono device and to reduce the 'right' input volume to 0%. Did that, still doesn't work.

3) Was playing around with Sound Recorder, and it did record a Youtube song that was playing. I paused the song and tried speaking. No sound. I guess this was internal recording.

Now, can someone please help me step-by-step to solve this issue?

Here's some info for starters:

Kernel: 2.6.32-27-generic ; Ubuntu 10.04

lspci:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

If you need more info, please tell me the command that I should put in the terminal and I will put the output here.

[http://www.alsa-project.org/db/?f=fec5227e09ecf5d508c619235148f85f1a4f5287](http://www.alsa-project.org/db/?f=fec5227e09ecf5d508c619235148f85f1a4f5287)

Thank you.

---

### Post by ideamaestro on 2011-01-09
Upgrading to 1.0.22 driver solved the problem with Linux_2.6.34.27_generic_pae kernel. However, the wireless driver is gone. Will try to solve this problem and post here.

Now, headphone, internal microphone, external microphone, all WORKS!!!

---

