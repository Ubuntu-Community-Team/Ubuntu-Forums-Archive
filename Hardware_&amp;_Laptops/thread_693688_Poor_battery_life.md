---
title: "Poor battery life"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by mevets on 2008-02-11
I have a gateway mx6931 ( [http://support.gateway.com/s/Mobile/Q106/BladeC/1013918Rsp2.shtml](http://support.gateway.com/s/Mobile/Q106/BladeC/1013918Rsp2.shtml) )

and I get about an hour less battery life under linux than I do in windows. I have heard that compiling my own kernel could increase my battery life. I understand this is quite a task, but I have plenty of other computers I can use while compiling and the time to spare. My question is, is this going to make much of a difference, should I even bother?

---

### Post by Navaja on 2008-02-11
I don't think that recompiling the kernel will make such a drastic difference in battery life. Have you acpi working?. Does scaling the cpu frequency works for you?. Try adding the "scale frequency monitor" applet (right click in the upper panel - Add to panel - scale frequency monitor, or something like that), and see if it shows that your cpu is not running at 100% all the time.

Also, you should run the command dmesg in a terminal and post the output,

---

### Post by mevets on 2008-02-11
services-admin says acpid and apmd are working.

dmesg:
```

[  150.412000] CPU: L1 I cache: 32K, L1 D cache: 32K
[  150.412000] CPU: L2 cache: 2048K
[  150.412000] CPU: Physical Processor ID: 0
[  150.412000] CPU: Processor Core ID: 1
[  150.412000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[  150.412000] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[  150.412000] CPU1 is up
[  150.416000] Switched to high resolution mode on CPU 1
[  150.420000] PM: Writing back config space on device 0000:00:02.0 at offset f (was 100, writing 10b)
[  150.436000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[  150.436000] PM: Writing back config space on device 0000:00:02.1 at offset 1 (was 900000, writing 900007)
[  150.452000] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 10)
[  150.452000] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100106, writing 100102)
[  150.452000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[  150.452000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  150.584000] PM: Writing back config space on device 0000:00:1c.0 at offset f (was 40100, writing 4010b)
[  150.584000] PM: Writing back config space on device 0000:00:1c.0 at offset 9 (was 10001, writing d1f1d001)
[  150.584000] PM: Writing back config space on device 0000:00:1c.0 at offset 8 (was 0, writing d5f0d400)
[  150.584000] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 20000000, writing 2020)
[  150.584000] PM: Writing back config space on device 0000:00:1c.0 at offset 6 (was 0, writing 20200)
[  150.584000] PM: Writing back config space on device 0000:00:1c.0 at offset 3 (was 810000, writing 810010)
[  150.584000] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100000, writing 100107)
[  150.584000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[  150.584000] PM: Writing back config space on device 0000:00:1c.1 at offset f (was 40200, writing 4020b)
[  150.584000] PM: Writing back config space on device 0000:00:1c.1 at offset 9 (was 10001, writing d3f1d201)
[  150.584000] PM: Writing back config space on device 0000:00:1c.1 at offset 8 (was 0, writing d7f0d600)
[  150.584000] PM: Writing back config space on device 0000:00:1c.1 at offset 7 (was 20000000, writing 3030)
[  150.584000] PM: Writing back config space on device 0000:00:1c.1 at offset 3 (was 810000, writing 810010)
[  150.584000] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100000, writing 100107)
[  150.584000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[  150.584000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[  150.584000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[  150.584000] usb usb1: root hub lost power or was reset
[  150.584000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[  150.584000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[  150.584000] usb usb2: root hub lost power or was reset
[  150.584000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[  150.584000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[  150.584000] usb usb3: root hub lost power or was reset
[  150.584000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[  150.584000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[  150.584000] usb usb4: root hub lost power or was reset
[  150.600000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[  150.600000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[  150.600000] PM: Writing back config space on device 0000:00:1e.0 at offset 9 (was 10001, writing 8bf18801)
[  150.600000] PM: Writing back config space on device 0000:00:1e.0 at offset 8 (was d8000000, writing d800d800)
[  150.600000] PM: Writing back config space on device 0000:00:1e.0 at offset 7 (was 228000f0, writing 22804040)
[  150.600000] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 20050400, writing 20080400)
[  150.600000] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100004, writing 100007)
[  150.600000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[  150.600000] PM: Writing back config space on device 0000:00:1f.0 at offset 1 (was 2100007, writing 2100107)
[  150.600000] PM: Writing back config space on device 0000:00:1f.1 at offset f (was 200, writing 2ff)
[  150.600000] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800000, writing 2800005)
[  150.600000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[  150.600000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[  150.600000] ata2: port disabled. ignoring.
[  150.616000] PM: Writing back config space on device 0000:00:1f.2 at offset f (was 200, writing 20a)
[  150.616000] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00005, writing 2b00007)
[  150.616000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[  150.616000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  151.256000] ata1.00: configured for UDMA/33
[  151.620000] PM: Writing back config space on device 0000:02:00.0 at offset f (was 100, writing 10b)
[  151.620000] PM: Writing back config space on device 0000:02:00.0 at offset 6 (was 1, writing 2001)
[  151.620000] PM: Writing back config space on device 0000:02:00.0 at offset 4 (was 4, writing d4000004)
[  151.620000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 10)
[  151.620000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 40100000, writing 100103)
[  151.620000] PM: Writing back config space on device 0000:03:00.0 at offset f (was 100, writing 10b)
[  151.620000] PM: Writing back config space on device 0000:03:00.0 at offset 4 (was 0, writing d6000000)
[  151.620000] PM: Writing back config space on device 0000:03:00.0 at offset 3 (was 0, writing 10)
[  151.620000] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100000, writing 100102)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset f (was 34001ff, writing 5c001ff)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset e (was 0, writing 44fc)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset d (was 0, writing 4400)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset c (was 0, writing 40fc)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset b (was 0, writing 4000)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset a (was 0, writing 8ffff000)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset 9 (was 0, writing 8c000000)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset 8 (was 0, writing 8bfff000)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset 7 (was 0, writing 88000000)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset 6 (was 0, writing b0080504)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset 4 (was 0, writing d8006000)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset 3 (was 820000, writing 82a820)
[  151.620000] PM: Writing back config space on device 0000:04:09.0 at offset 1 (was 2100000, writing 2100007)
[  151.636000] PM: Writing back config space on device 0000:04:09.1 at offset f (was 4030200, writing 403020b)
[  151.636000] PM: Writing back config space on device 0000:04:09.1 at offset 5 (was 0, writing d8000000)
[  151.636000] PM: Writing back config space on device 0000:04:09.1 at offset 4 (was 0, writing d8005000)
[  151.636000] PM: Writing back config space on device 0000:04:09.1 at offset 3 (was 800000, writing 804000)
[  151.636000] PM: Writing back config space on device 0000:04:09.1 at offset 1 (was 2100000, writing 2100006)
[  151.684000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[d8005000-d80057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[  151.700000] PM: Writing back config space on device 0000:04:09.2 at offset f (was 40701ff, writing 407010b)
[  151.700000] PM: Writing back config space on device 0000:04:09.2 at offset 4 (was 0, writing d8004000)
[  151.700000] PM: Writing back config space on device 0000:04:09.2 at offset 3 (was 800000, writing 804000)
[  151.700000] PM: Writing back config space on device 0000:04:09.2 at offset 1 (was 2100000, writing 2100006)
[  151.700000] ACPI: PCI Interrupt 0000:04:09.2[A] -> GSI 17 (level, low) -> IRQ 16
[  151.700000] pnp: Failed to activate device 00:08.
[  151.932000] ata4: SATA link down (SStatus 0 SControl 0)
[  151.932000] ata5: SATA link down (SStatus 0 SControl 300)
[  151.932000] ata6: SATA link down (SStatus 0 SControl 0)
[  152.160000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  152.168000] ata3.00: configured for UDMA/100
[  152.168000] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  152.168000] sd 2:0:0:0: [sda] Write Protect is off
[  152.168000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  152.168000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  152.428000] usb_endpoint usbdev5.1_ep00: PM: resume from 0, parent usb5 still 2
[  152.428000] usb_endpoint usbdev5.1_ep81: PM: resume from 0, parent 5-0:1.0 still 2
[  152.428000] usb_device usbdev5.1: PM: resume from 0, parent usb5 still 2
[  152.428000] sd 2:0:0:0: [sda] Starting disk
[  152.444000] Restarting tasks ... done.
[  167.936000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[  167.936000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[  167.936000] sky2 0000:02:00.0: v1.18 addr 0xd4000000 irq 17 Yukon-FE (0xb7) rev 1
[  167.936000] sky2 eth0: addr 00:e0:b8:c0:ca:05
[  167.940000] ieee80211_crypt: registered algorithm 'NULL'
[  167.956000] sky2 eth0: enabling interface
[  167.960000] bridge-eth0: enabling the bridge
[  167.960000] bridge-eth0: up
[  167.960000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  167.960000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  167.968000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[  167.968000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[  167.968000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[  167.968000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  167.968000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[  168.784000] input: Power Button (FF) as /class/input/input9
[  168.784000] ACPI: Power Button (FF) [PWRF]
[  168.788000] input: Power Button (CM) as /class/input/input10
[  168.788000] ACPI: Power Button (CM) [PWRB]
[  168.808000] input: Sleep Button (CM) as /class/input/input11
[  168.808000] ACPI: Sleep Button (CM) [SLPB]
[  168.816000] input: Lid Switch as /class/input/input12
[  168.816000] ACPI: Lid Switch [LID]
[  168.984000] ACPI: Thermal Zone [TZ00] (52 C)
[  169.048000] ACPI: AC Adapter [ACAD] (off-line)
[  169.092000] ACPI: Battery Slot [BAT1] (battery present)
[  169.756000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[ 3319.108000] sky2 eth0: disabling interface
[ 3319.112000] bridge-eth0: disabling the bridge
[ 3319.136000] bridge-eth0: down
[ 3319.376000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[ 3322.432000] PM: Preparing system for mem sleep
[ 3322.432000] Stopping tasks ... done.
[ 3323.200000] Suspending console(s)
[ 3323.200000] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 3323.476000] sd 2:0:0:0: [sda] Stopping disk
[ 3323.976000] usb_device usbdev5.1: PM: suspend 0->2, parent usb5 already 2
[ 3323.976000] usb_endpoint usbdev5.1_ep81: PM: suspend 0->2, parent 5-0:1.0 already 2
[ 3323.976000] hub 5-0:1.0: PM: suspend 2->2, parent usb5 already 2
[ 3323.976000] usb_endpoint usbdev5.1_ep00: PM: suspend 0->2, parent usb5 already 2
[ 3323.976000] usb_device usbdev4.1: PM: suspend 0->2, parent usb4 already 2
[ 3323.976000] usb_endpoint usbdev4.1_ep81: PM: suspend 0->2, parent 4-0:1.0 already 2
[ 3323.976000] hub 4-0:1.0: PM: suspend 2->2, parent usb4 already 2
[ 3323.976000] usb_endpoint usbdev4.1_ep00: PM: suspend 0->2, parent usb4 already 2
[ 3323.976000] usb_device usbdev3.1: PM: suspend 0->2, parent usb3 already 2
[ 3323.976000] usb_endpoint usbdev3.1_ep81: PM: suspend 0->2, parent 3-0:1.0 already 2
[ 3323.976000] hub 3-0:1.0: PM: suspend 2->2, parent usb3 already 2
[ 3323.976000] usb_endpoint usbdev3.1_ep00: PM: suspend 0->2, parent usb3 already 2
[ 3323.976000] usb_device usbdev2.1: PM: suspend 0->2, parent usb2 already 2
[ 3323.976000] usb_endpoint usbdev2.1_ep81: PM: suspend 0->2, parent 2-0:1.0 already 2
[ 3323.976000] hub 2-0:1.0: PM: suspend 2->2, parent usb2 already 2
[ 3323.976000] usb_endpoint usbdev2.1_ep00: PM: suspend 0->2, parent usb2 already 2
[ 3323.976000] usb_device usbdev1.1: PM: suspend 0->2, parent usb1 already 2
[ 3323.976000] usb_endpoint usbdev1.1_ep81: PM: suspend 0->2, parent 1-0:1.0 already 2
[ 3323.976000] hub 1-0:1.0: PM: suspend 2->2, parent usb1 already 2
[ 3323.976000] usb_endpoint usbdev1.1_ep00: PM: suspend 0->2, parent usb1 already 2
[ 3324.588000] ACPI: PCI interrupt for device 0000:04:09.2 disabled
[ 3324.620000] eth1: Going into suspend...
[ 3324.728000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[ 3324.744000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[ 3324.760000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[ 3324.760000] pci_set_power_state(): 0000:00:1f.1: state=3, current state=5
[ 3324.760000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[ 3324.776000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[ 3324.776000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[ 3324.776000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[ 3324.776000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[ 3324.784000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 3324.800000] Disabling non-boot CPUs ...
[ 3324.916000] CPU 1 is now offline
[ 3324.916000] SMP alternatives: switching to UP code
[ 3324.916000] CPU1 is down
[ 3324.916000] PM: Entering mem sleep
[ 3324.916000] Back to C!
[ 3324.916000] PM: Finishing wakeup.
[ 3324.916000] Enabling non-boot CPUs ...
[ 3324.928000] SMP alternatives: switching to SMP code
[ 3324.928000] Booting processor 1/1 eip 3000
[ 3324.936000] Initializing CPU#1
[ 3325.016000] Calibrating delay using timer specific routine.. 3326.11 BogoMIPS (lpj=6652228)
[ 3325.016000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[ 3325.016000] monitor/mwait feature present.
[ 3325.016000] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 3325.016000] CPU: L2 cache: 2048K
[ 3325.016000] CPU: Physical Processor ID: 0
[ 3325.016000] CPU: Processor Core ID: 1
[ 3325.016000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[ 3325.016000] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[ 3325.016000] CPU1 is up
[ 3325.020000] Switched to high resolution mode on CPU 1
[ 3325.024000] PM: Writing back config space on device 0000:00:02.0 at offset f (was 100, writing 10b)
[ 3325.040000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[ 3325.040000] PM: Writing back config space on device 0000:00:02.1 at offset 1 (was 900000, writing 900007)
[ 3325.056000] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 10)
[ 3325.056000] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100106, writing 100102)
[ 3325.056000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[ 3325.056000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.0 at offset f (was 40100, writing 4010b)
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.0 at offset 9 (was 10001, writing d1f1d001)
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.0 at offset 8 (was 0, writing d5f0d400)
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 20000000, writing 20002020)
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.0 at offset 6 (was 0, writing 20200)
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.0 at offset 3 (was 810000, writing 810010)
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100000, writing 100107)
[ 3325.188000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.1 at offset f (was 40200, writing 4020b)
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.1 at offset 9 (was 10001, writing d3f1d201)
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.1 at offset 8 (was 0, writing d7f0d600)
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.1 at offset 7 (was 20000000, writing 20003030)
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.1 at offset 3 (was 810000, writing 810010)
[ 3325.188000] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100000, writing 100107)
[ 3325.188000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[ 3325.188000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[ 3325.188000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 3325.188000] usb usb1: root hub lost power or was reset
[ 3325.188000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[ 3325.188000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[ 3325.188000] usb usb2: root hub lost power or was reset
[ 3325.188000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[ 3325.188000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[ 3325.188000] usb usb3: root hub lost power or was reset
[ 3325.188000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[ 3325.188000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[ 3325.188000] usb usb4: root hub lost power or was reset
[ 3325.204000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[ 3325.204000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[ 3325.204000] PM: Writing back config space on device 0000:00:1e.0 at offset 9 (was 10001, writing 8bf18801)
[ 3325.204000] PM: Writing back config space on device 0000:00:1e.0 at offset 8 (was d8000000, writing d800d800)
[ 3325.204000] PM: Writing back config space on device 0000:00:1e.0 at offset 7 (was 228000f0, writing 22804040)
[ 3325.204000] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 20050400, writing 20080400)
[ 3325.204000] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100004, writing 100007)
[ 3325.204000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 3325.204000] PM: Writing back config space on device 0000:00:1f.0 at offset 1 (was 2100007, writing 2100107)
[ 3325.204000] PM: Writing back config space on device 0000:00:1f.1 at offset f (was 200, writing 2ff)
[ 3325.204000] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800000, writing 2800005)
[ 3325.204000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[ 3325.204000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 3325.204000] ata2: port disabled. ignoring.
[ 3325.220000] PM: Writing back config space on device 0000:00:1f.2 at offset f (was 200, writing 20a)
[ 3325.220000] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00005, writing 2b00007)
[ 3325.220000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[ 3325.220000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[ 3325.860000] ata1.00: configured for UDMA/33
[ 3326.224000] PM: Writing back config space on device 0000:02:00.0 at offset f (was 100, writing 10b)
[ 3326.224000] PM: Writing back config space on device 0000:02:00.0 at offset 6 (was 1, writing 2001)
[ 3326.224000] PM: Writing back config space on device 0000:02:00.0 at offset 4 (was 4, writing d4000004)
[ 3326.224000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 10)
[ 3326.224000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 40100000, writing 100103)
[ 3326.224000] eth1: Coming out of suspend...
[ 3326.240000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[ 3326.240000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[ 3326.240000] PM: Writing back config space on device 0000:03:00.0 at offset f (was 100, writing 10b)
[ 3326.240000] PM: Writing back config space on device 0000:03:00.0 at offset 4 (was 0, writing d6000000)
[ 3326.240000] PM: Writing back config space on device 0000:03:00.0 at offset 3 (was 0, writing 10)
[ 3326.240000] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100002, writing 100106)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset f (was 34001ff, writing 5c001ff)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset e (was 0, writing 44fc)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset d (was 0, writing 4400)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset c (was 0, writing 40fc)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset b (was 0, writing 4000)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset a (was 0, writing 8ffff000)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset 9 (was 0, writing 8c000000)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset 8 (was 0, writing 8bfff000)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset 7 (was 0, writing 88000000)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset 6 (was 0, writing b0080504)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset 4 (was 0, writing d8006000)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset 3 (was 820000, writing 82a820)
[ 3326.240000] PM: Writing back config space on device 0000:04:09.0 at offset 1 (was 2100000, writing 2100007)
[ 3326.256000] PM: Writing back config space on device 0000:04:09.1 at offset f (was 4030200, writing 403020b)
[ 3326.256000] PM: Writing back config space on device 0000:04:09.1 at offset 5 (was 0, writing d8000000)
[ 3326.256000] PM: Writing back config space on device 0000:04:09.1 at offset 4 (was 0, writing d8005000)
[ 3326.256000] PM: Writing back config space on device 0000:04:09.1 at offset 3 (was 800000, writing 804000)
[ 3326.256000] PM: Writing back config space on device 0000:04:09.1 at offset 1 (was 2100000, writing 2100006)
[ 3326.304000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[d8005000-d80057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[ 3326.320000] PM: Writing back config space on device 0000:04:09.2 at offset f (was 40701ff, writing 407010b)
[ 3326.320000] PM: Writing back config space on device 0000:04:09.2 at offset 4 (was 0, writing d8004000)
[ 3326.320000] PM: Writing back config space on device 0000:04:09.2 at offset 3 (was 800000, writing 804000)
[ 3326.320000] PM: Writing back config space on device 0000:04:09.2 at offset 1 (was 2100000, writing 2100006)
[ 3326.320000] ACPI: PCI Interrupt 0000:04:09.2[A] -> GSI 17 (level, low) -> IRQ 16
[ 3326.320000] pnp: Failed to activate device 00:08.
[ 3326.536000] ata4: SATA link down (SStatus 0 SControl 0)
[ 3326.536000] ata5: SATA link down (SStatus 0 SControl 300)
[ 3326.536000] ata6: SATA link down (SStatus 0 SControl 0)
[ 3326.708000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 3326.724000] ata3.00: configured for UDMA/100
[ 3326.724000] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 3326.724000] sd 2:0:0:0: [sda] Write Protect is off
[ 3326.724000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3326.724000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3327.080000] usb_endpoint usbdev5.1_ep00: PM: resume from 0, parent usb5 still 2
[ 3327.080000] usb_endpoint usbdev5.1_ep81: PM: resume from 0, parent 5-0:1.0 still 2
[ 3327.080000] usb_device usbdev5.1: PM: resume from 0, parent usb5 still 2
[ 3327.080000] sd 2:0:0:0: [sda] Starting disk
[ 3327.100000] Restarting tasks ... done.
[ 3339.276000] usb 2-1: new low speed USB device using uhci_hcd and address 4
[ 3348.800000] usb 2-1: configuration #1 chosen from 1 choice
[ 3348.816000] input: Logitech USB Receiver as /class/input/input13
[ 3348.816000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1
[ 3348.844000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor
[ 3348.848000] input: Logitech USB Receiver as /class/input/input14
[ 3348.848000] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[ 3349.096000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[ 3349.096000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[ 3349.096000] sky2 0000:02:00.0: v1.18 addr 0xd4000000 irq 17 Yukon-FE (0xb7) rev 1
[ 3349.096000] sky2 eth0: addr 00:e0:b8:c0:ca:05
[ 3349.180000] sky2 eth0: enabling interface
[ 3349.184000] bridge-eth0: enabling the bridge
[ 3349.184000] bridge-eth0: up
[ 3349.420000] input: Power Button (FF) as /class/input/input15
[ 3349.420000] ACPI: Power Button (FF) [PWRF]
[ 3349.436000] input: Power Button (CM) as /class/input/input16
[ 3349.436000] ACPI: Power Button (CM) [PWRB]
[ 3349.436000] input: Sleep Button (CM) as /class/input/input17
[ 3349.436000] ACPI: Sleep Button (CM) [SLPB]
[ 3349.440000] input: Lid Switch as /class/input/input18
[ 3349.440000] ACPI: Lid Switch [LID]
[ 3349.564000] ACPI: Thermal Zone [TZ00] (43 C)
[ 3349.676000] ACPI: AC Adapter [ACAD] (on-line)
[ 3349.732000] ACPI: Battery Slot [BAT1] (battery present)
[ 3352.244000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both

```

---

### Post by PurposeOfReason on 2008-02-11
It really depends what you're changing when you recomplie the kernel. Could you post what you plan on doing?

---

### Post by mevets on 2008-02-11
Not even sure what I'd be able to change. Am I wrong to think theres anything to change?

---

### Post by neocortex on 2008-02-11
Hi all!
I have a similar problem with my HP nx8220. Battery life is poor, and my fan is always on. What to do? How to check if my acpi is working properly? I run dmesg, but I got just a lot of unreadable strings.

Best,
PM

---

### Post by unrater on 2008-04-17
i have the same problem in ubuntu 7.10. but in other old releases i did not have that problem.

and the acpi is ON and always in POWERSAVE.

i think the problem is in memory and disk. Disk because of that problem of super rotation, and memory because I always I 500+MB :S

---

