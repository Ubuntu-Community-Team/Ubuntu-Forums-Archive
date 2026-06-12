---
title: "HIbernate does shutdown instead"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by stenka on 2006-06-28
I suscribed the following bug on launchpad :

Bug #51179

<<
Binary package hint: acpi

I am on Dapper up-to-date. My computer is a Sony laptop from the FS series.

Sometimes, when I choose Hibernate, the computer totally shutdown instead of hibernating, although the whole process looks to be as normal as usual.

Here is my dmesg during the hibernation process :

Jun 27 23:17:38 localhost kernel: [17262268.092000] Stopping tasks: =====================================================================================================================================================================================|
Jun 27 23:17:42 localhost kernel: [17262268.380000] Shrinking memory... ^H-^H\^H|^H/^H-^Hdone (67330 pages freed)
Jun 27 23:17:42 localhost kernel: [17262296.528000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 659)
Jun 27 23:17:42 localhost kernel: [17262296.576000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 661)
Jun 27 23:17:42 localhost kernel: [17262297.116000] ACPI: PCI interrupt for device 0000:06:03.0 disabled
Jun 27 23:17:42 localhost kernel: [17262297.116000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Jun 27 23:17:42 localhost kernel: [17262297.132000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Jun 27 23:17:42 localhost kernel: [17262297.132000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Jun 27 23:17:42 localhost kernel: [17262297.132000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Jun 27 23:17:42 localhost kernel: [17262297.132000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Jun 27 23:17:42 localhost kernel: [17262297.148000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Jun 27 23:17:42 localhost kernel: [17262297.148000] swsusp: Need to copy 54970 pages
Jun 27 23:17:42 localhost kernel: [17262297.148000] swsusp: Restoring Highmem
Jun 27 23:17:42 localhost kernel: [17274182.200000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
Jun 27 23:17:42 localhost kernel: [17274182.200000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
Jun 27 23:17:42 localhost kernel: [17274182.284000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 185
Jun 27 23:17:42 localhost kernel: [17274182.284000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
Jun 27 23:17:42 localhost kernel: [17274182.284000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
Jun 27 23:17:42 localhost kernel: [17274182.284000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
Jun 27 23:17:42 localhost kernel: [17274182.300000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Jun 27 23:17:42 localhost kernel: [17274182.300000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 185
Jun 27 23:17:42 localhost kernel: [17274182.300000] ehci_hcd 0000:00:1d.7: debug port 1
Jun 27 23:17:42 localhost kernel: [17274182.304000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 27 23:17:43 localhost kernel: [17274182.304000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
Jun 27 23:17:43 localhost kernel: [17274182.308000] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 16 (level, low) -> IRQ 169
Jun 27 23:17:43 localhost kernel: [17274182.308000] ACPI: PCI Interrupt 0000:06:03.2[C] -> GSI 18 (level, low) -> IRQ 177
Jun 27 23:17:43 localhost kernel: [17274182.956000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 648)
Jun 27 23:17:43 localhost kernel: [17274183.004000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 659)
Jun 27 23:17:43 localhost kernel: [17274183.052000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 661)
Jun 27 23:17:43 localhost kernel: [17274183.100000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 648)
Jun 27 23:17:43 localhost kernel: [17274183.100000] Restarting tasks... done
Jun 27 23:17:43 localhost kernel: [17274184.568000] input: PS/2 Mouse as /class/input/input11
Jun 27 23:17:43 localhost kernel: [17274184.588000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input12
Jun 27 23:17:56 localhost kernel: [17274205.284000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
Jun 27 23:17:56 localhost kernel: [17274205.284000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jun 27 23:17:56 localhost kernel: [17274205.292000] ieee80211: 802.11 data/management/control stack, git-1.1.7
Jun 27 23:17:56 localhost kernel: [17274205.292000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jun 27 23:17:56 localhost kernel: [17274205.988000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
Jun 27 23:17:56 localhost kernel: [17274205.988000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jun 27 23:17:56 localhost kernel: [17274205.988000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
Jun 27 23:17:56 localhost kernel: [17274205.988000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 22 (level, low) -> IRQ 209
Jun 27 23:17:56 localhost kernel: [17274205.988000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jun 27 23:17:59 localhost kernel: [17274208.504000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
Jun 27 23:18:00 localhost kernel: [17274209.108000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
Jun 27 23:18:00 localhost kernel: [17274209.108000] e100: Copyright(c) 1999-2005 Intel Corporation
Jun 27 23:18:00 localhost kernel: [17274209.108000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 201
Jun 27 23:18:00 localhost kernel: [17274209.144000] e100: eth1: e100_probe: addr 0xb0107000, irq 201, MAC addr 00:01:4A:5C:51:D5
Jun 27 23:18:02 localhost pppd[26405]: Exit.
Jun 27 23:18:04 localhost kernel: [17274215.152000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 27 23:18:07 localhost kernel: [17274218.380000] ACPI: Power Button (FF) [PWRF]
Jun 27 23:18:07 localhost kernel: [17274218.380000] ACPI: Lid Switch [LID0]
Jun 27 23:18:07 localhost kernel: [17274218.380000] ACPI: Power Button (CM) [PWRB]
Jun 27 23:18:10 localhost kernel: [17274221.132000] ACPI: CPU0 (power states: C1[C1] C2[C2])
Jun 27 23:18:11 localhost kernel: [17274221.132000] ACPI: Processor [CPU0] (supports 8 throttling states)
Jun 27 23:18:11 localhost kernel: [17274221.956000] ACPI: Thermal Zone [THRM] (41 C)
Jun 27 23:18:11 localhost kernel: [17274222.504000] ACPI: AC Adapter [ADP1] (on-line)
Jun 27 23:18:12 localhost kernel: [17274222.712000] ACPI: Battery Slot [BAT0] (battery present)
Jun 27 23:18:16 localhost kernel: [17274226.784000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Jun 27 23:18:53 localhost kernel: [17274264.348000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 27 23:19:00 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun 27 23:19:00 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 27 23:19:00 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 27 23:33:43 localhost -- MARK --
Jun 27 23:53:43 localhost -- MARK --
Jun 27 23:58:53 localhost kernel: [17276658.548000] ACPI: PCI interrupt for device 0000:06:04.0 disabled
Jun 27 23:58:53 localhost kernel: [17276658.588000] ACPI: PCI interrupt for device 0000:06:08.0 disabled

Always concerning ACPI, I sometimes get some warning messages from Network Manager, when I wake up my computer. It says something related to ACPI didn't go well but I can't tell what.
>>

If someone has the same issue or has an idea...

---

### Post by ahaslam on 2006-06-28
Lots of us are having similar problems. My laptop will hibernate but upon reboot I'm greeted with a garbled screen, unable to see or do anything. See my thread [here]("http://ubuntuforums.org/showthread.php?t=183616").
Sorry I can't help,

Tony.

---

