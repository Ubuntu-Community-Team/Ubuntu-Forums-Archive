---
title: "Can't mount SD card"
date: 2009-05-26
forum: Hardware
---

### Post by SirSigma on 2009-05-26
Okay, I'm really desperate now. I've searched and have had no luck, so I'll try to be very specific.

I'm using Jaunty and want to mount my SD card using my integrated card reader on my laptop. When I first purchased the 2GB Sandisk SD card two days ago, the first thing I did was open it and plug it in while running Jaunty. The problem? Doesn't work. 

I guessed my card may have been damaged in some way, so I tried using it on Windows 7. The first time I tried using it on Windows 7 gave me severe problems with speed on the system. I tried it on my 60GB PS3 integrated card reader and it worked just fine. After coming to the conclusion the SD card is not damaged, I tried using it again on Windows 7 and it works perfectly.

I've read the threads below and tried implementing most of the things they've mentioned

[http://ubuntuforums.org/showthread.php?t=299939](http://ubuntuforums.org/showthread.php?t=299939)
[http://ubuntuforums.org/showthread.php?t=1166737](http://ubuntuforums.org/showthread.php?t=1166737)
[http://ubuntuforums.org/showthread.php?t=1146962](http://ubuntuforums.org/showthread.php?t=1146962)

And if you're wondering why I didn't list more threads from the search, it's not that I'm only partly reading the SD card or something like that. I can't mount the SD card at all. It doesn't show up at all.

I tried using the modprobe command on the second page of the first link, but that didn't seem to do anything at all, and now I'm scared I might have changed something important without meaning to. I tried commenting out the specified lines on /fstab (like one of the links says), but only one of those mentioned lines was on the file, and it made no difference when I commented it out, so I set it back to the way it was.

This part may not be important, but it might also help to mention that a few days ago I booted into Ubuntu with the SD card in the slot (if I recall correctly), and after logging in, was given a completely black screen. I rebooted by pressing the button and tried again, but I pulled the SD card while it booted, and I ended up with Ubuntu saying it failed to boot and was going to restart. After it restarted, I went into the recovery boot, but didn't do anything except resume normal boot. Then it worked.

Anyway, I really need help at this point.

Here's my lspci

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

and if anybody want to know dmesg|tail, it doesn't really help since this is all I get

```
[13330.296756] ath5k phy0: noise floor calibration timeout (2462MHz)
[13448.760371] ath5k phy0: noise floor calibration timeout (2457MHz)
[13449.157701] ath5k phy0: noise floor calibration timeout (2462MHz)
[13449.533842] ath5k phy0: noise floor calibration timeout (2467MHz)
[13450.628572] ath5k phy0: noise floor calibration timeout (2462MHz)
[13569.040559] ath5k phy0: noise floor calibration timeout (2462MHz)
[13569.439286] ath5k phy0: noise floor calibration timeout (2467MHz)
[13570.525060] ath5k phy0: noise floor calibration timeout (2462MHz)
[13689.080238] ath5k phy0: noise floor calibration timeout (2462MHz)
[13689.453253] ath5k phy0: noise floor calibration timeout (2467MHz)

```

So in addition, I'm going to post the last lines of dmesg before I get that long repeating set of ath5k messages

```
[   30.052697] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.052701] Bluetooth: BNEP filters: protocol multicast
[   30.065634] Bridge firewalling registered
[   31.366290] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   31.640260] [drm] Initialized drm 1.1.0 20060810
[   31.689342] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   31.719000] ppdev: user-space parallel port driver
[   32.711858] [drm] Setting GART location based on new memory map
[   32.712544] [drm] Loading RS690/RS740 Microcode
[   32.712563] [drm] Num pipes: 1
[   32.712570] [drm] writeback test succeeded in 1 usecs
[   36.101149] r8169: eth0: link down
[   36.101375] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.129043] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   54.243016] CPU0 attaching NULL sched-domain.
[   54.243023] CPU1 attaching NULL sched-domain.
[   54.275249] CPU0 attaching sched-domain:
[   54.275254]  domain 0: span 0-1 level CPU
[   54.275257]   groups: 0 1
[   54.275264] CPU1 attaching sched-domain:
[   54.275266]  domain 0: span 0-1 level CPU
[   54.275268]   groups: 1 0
[   55.552566] wlan0: authenticate with AP 00:1d:7e:ed:d5:50
[   55.554156] wlan0: authenticated
[   55.554160] wlan0: associate with AP 00:1d:7e:ed:d5:50
[   55.556281] wlan0: RX AssocResp from 00:1d:7e:ed:d5:50 (capab=0x411 status=0 aid=2)
[   55.556284] wlan0: associated
[   55.557625] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   65.920025] wlan0: no IPv6 routers present
[   94.000052] Clocksource tsc unstable (delta = -300566180 ns)
[ 1311.705646] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1445.517309] CE: hpet increasing min_delta_ns to 22500 nsec
[ 1925.144945] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

```

If any other information is needed, please let me know.

---

### Post by SirSigma on 2009-05-26
I still need help on this. Please?

---

### Post by SirSigma on 2009-05-26
Hello? :(

---

### Post by SirSigma on 2009-05-27
This is getting ridiculous.

---

### Post by MBro on 2009-06-01
I don't have a solution but I also have the same problem as you and cannot figure it out.

---

### Post by warpasylum on 2009-06-13
same issue here with a micro sd card on jaunty.  mounts fine on my laptop running intrepid, guess it might be the card reader.

---

### Post by jodiemaceachern on 2009-06-13
I had the issue, I do not understand what was wrong, but I did a lsmod, and there not very many modules loaded. My installation was bad some how. 
What I did was reloaded Ubuntu, and it started working.

What I was doing before was, **not** formatting the partition before the install. So to get it to work I needed to allow the Ubuntu install to format the partition.

You could boot from a live CD and try the SD card. See if it works running from the Live CD.

---

### Post by warpasylum on 2009-06-14
Hey guys,
     Figured out the issue with my reader.... human error. The cards have to go in upside-down. Reads 'em just fine now. Kickin' myself in the teeth as I figure this out 14 hours later. Good luck.

---

