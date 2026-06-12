---
title: "Macbook Pro 9,2 sleeps when left alone for 10 minutes - doesn't come back up"
date: 2014-08-30
forum: Hardware
---

### Post by brittany2 on 2014-08-30
Power settings set to:
on AC: put the computer to sleep when inactive for 5 hours 50 minutes. Monitor: put display to sleep when computer is inactive for 60 minutes, switch off display when computer inactive for 50 minutes. Reduce brightness when computer inactive for Never.

I am running on AC currently. Computer sleeps after 10 minutes of inactivity. Luckily while I am watching Netflix I am right there to wake it up before it fully sleeps. But when I step away with a video paused or even not in an active video the computer will sleep but there is no way to wake it. I end up pressing the power button. Then I press it again as I get no response and it boots up the computer.

The Extended options in Power Manager are: Set computer inactivity sleep mode: Suspend (only available option), Set monitor sleep mode Standby. Consider the computer low on power at 10% (currently at 99%), Lock screen when going for suspend/hibernate is enabled.

I am very frustrated by this problem. I am using the newest LTS release that just updated yesterday evening or this morning (can't recall which it was) and I did have this problem yesterday as well, before the update.

```
 brittany@xubuntumbp:~$ lsusbBus 002 Device 006: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 002 Device 005: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 009: ID 05ac:821d Apple, Inc. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0951:1624 Kingston Technology DataTraveler G2
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
 brittany@xubuntumbp:~$ lspci00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe (rev 10)
01:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 10)
02:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
03:00.0 FireWire (IEEE 1394): LSI Corporation FW643 [TrueFire] PCIe 1394b Controller (rev 08)
brittany@xubuntumbp:~$ 

```

I see this in dmesg:  6.007935] init: udev-fallback-graphics main process (732) terminated with status 1
I do not know if it has any bearing on my current problem.

And this looks relavent:
```
 [    5.779089] apple 0003:05AC:0252.0003: hidraw2: USB HID v1.11 Device [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.0-1.8.3/input1
[    5.836173] Console: switching to colour frame buffer device 160x50
[    5.837857] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    5.837858] i915 0000:00:02.0: registered panic notifier
[    5.844691] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    5.844897] acpi device:0e: registered as cooling_device5
[    5.844964] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
[    5.846282] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    5.848338] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    5.848344] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.848348] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    5.848351] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.848353] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    5.848355] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.848356] lpc_ich: Resource conflict(s) found affecting gpio_ich

```

I am not sure if I need to install something to fix this or edit a file. If anything can be done to fix this, please let me know what you need from me to help you help me.

Thank you, all.

Brittany

---

