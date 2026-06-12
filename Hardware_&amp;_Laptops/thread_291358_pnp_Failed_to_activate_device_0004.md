---
title: "pnp: Failed to activate device 00:04  ??"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by lagartoflojo on 2006-11-02
Hi!
   I just installed Edgy over my installation of Dapper (upgrading didn't go so well...) and there is a little 'glitch' that apparently doesn't affect the computer, really, but I'd like to know its source. (This didn't happen in Dapper).

   The thing is, that when I resume my laptop (Alienware m5500) after I suspend it, before Gnome comes up, the console reads:
```
[17180665.692000] pnp: Failed to activate device 00:04.
[17180665.692000] pnp: Failed to activate device 00:05.
```

The pertinent (I think...) output of dmesg is:

```
[17180663.416000] NVRM: RmPowerManagement: 4
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset f (was 34001ff, writing 5c00107)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset e (was 0, writing c4fc)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset d (was 0, writing c400)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset c (was 0, writing c0fc)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset b (was 0, writing c000)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset a (was 0, writing 33fff000)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset 9 (was 0, writing 32000000)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset 8 (was 0, writing 31fff000)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset 7 (was 0, writing 30000000)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset 6 (was 40000000, writing b0020201)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset 4 (was 0, writing f4100000)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset 3 (was 20000, writing 2a820)
[17180665.692000] PM: Writing back config space on device 0000:01:03.0 at offset 1 (was 2100000, writing 2100007)
[17180665.692000] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 17 (level, low) -> IRQ 177
[17180665.692000] PM: Writing back config space on device 0000:01:07.0 at offset f (was 18030100, writing 18030103)
[17180665.692000] PM: Writing back config space on device 0000:01:07.0 at offset 4 (was 0, writing f49fe000)
[17180665.692000] PM: Writing back config space on device 0000:01:07.0 at offset 3 (was 0, writing 4008)
[17180665.692000] PM: Writing back config space on device 0000:01:07.0 at offset 1 (was 2900000, writing 2900002)
[17180665.692000] PM: Writing back config space on device 0000:01:0a.0 at offset f (was 4030100, writing 4030105)
[17180665.692000] PM: Writing back config space on device 0000:01:0a.0 at offset 5 (was 0, writing f49f8000)
[17180665.692000] PM: Writing back config space on device 0000:01:0a.0 at offset 4 (was 0, writing f49ff000)
[17180665.692000] PM: Writing back config space on device 0000:01:0a.0 at offset 3 (was 0, writing 4008)
[17180665.692000] PM: Writing back config space on device 0000:01:0a.0 at offset 1 (was 2100000, writing 2100016)
[17180665.692000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> GSI 18 (level, low) -> IRQ 217
[17180665.692000] PM: Writing back config space on device 0000:01:0c.0 at offset 5 (was 0, writing f49ffc00)
[17180665.692000] PM: Writing back config space on device 0000:01:0c.0 at offset 4 (was 1, writing d801)
[17180665.692000] PM: Writing back config space on device 0000:01:0c.0 at offset 3 (was 0, writing 4008)
[17180665.692000] PM: Writing back config space on device 0000:01:0c.0 at offset 1 (was 2b00000, writing 2b00013)
[b][17180665.692000] pnp: Failed to activate device 00:04.
[17180665.692000] pnp: Failed to activate device 00:05.[/b]
[17180666.292000] ata1: dev 0 configured for UDMA/100
[17180666.456000] ata2: dev 0 configured for UDMA/33
[17180666.632000] Restarting tasks...<6>usb 2-1: USB disconnect, address 2
[17180666.684000]  done
[17180666.684000] Thawing cpus ...
[17180667.284000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[17180667.460000] usb 2-1: configuration #1 chosen from 1 choice
[17180667.476000] input: Genius       Optical Mouse as /class/input/input4
[17180667.476000] input: USB HID v1.10 Mouse [Genius       Optical Mouse] on usb-0000:00:1d.1-1
[17180667.896000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17180667.896000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> GSI 19 (level, low) -> IRQ 201
[17180667.896000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17180667.896000] eth0: RTL8169 at 0xe0a7cc00, 00:03:0d:39:6d:94, IRQ 201
[17180667.932000] ieee80211_crypt: registered algorithm 'NULL'
[17180667.932000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17180667.932000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17180667.936000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17180667.936000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17180667.936000] Driver 'ipw2200' needs updating - please use bus_type methods
[17180667.936000] ACPI: PCI Interrupt 0000:01:07.0[A] -> GSI 19 (level, low) -> IRQ 201
[17180667.936000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[17180668.120000] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[17180668.136000] r8169: eth0: link down
[17180668.136000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180668.156000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.
[17180670.196000] ACPI: Power Button (FF) [PWRF]
[17180670.196000] ACPI: Lid Switch [LID]
[17180670.196000] ACPI: Sleep Button (CM) [SLPB]
[17180670.196000] ACPI: Power Button (CM) [PWRB]
[17180670.288000] ACPI: Thermal Zone [THRM] (62 C)
[17180670.348000] ACPI: AC Adapter [AC0] (on-line)
[17180670.448000] ACPI: Battery Slot [BAT0] (battery present)
[17180680.084000] eth1: no IPv6 routers present
```
(there's more, if needed).

the output of lspci is
```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
01:07.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
03:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6600] (rev a2)
```


There are no devices 00:04 or 00:05!!

After the computer resumes, there are no apparent problems  (I am writing this after a resume, and at least wifi is working...)

Any ideas?

---

### Post by MrBobby on 2006-12-08
I am having this same problem on a recently upgraded laptop. Unlike original poster, my installation went flawlessly - the computer is almost unused. Yet the error is the same.

---

