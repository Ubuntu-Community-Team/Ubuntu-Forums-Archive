---
title: "Please help me debug suspend for Acer Aspire"
date: 2008-06-26
forum: Hardware
---

### Post by tillkowski on 2008-06-26
Hi -

I'm running a standard Ubuntu install (with encrypted LVM) on an Acer Laptop. Everything works great, except for suspend to RAM.

I read the [debugging guide](http://ubuntuforums.org/showthread.php?p=3066404) but my case seems to be a little different, and I don't know where to go from here.

Suspend to RAM worked a total of three times for me, but all the other times I tried (maybe 20 or so) this happens: The laptop seems to go to sleep, the lights blink red, but when I press the space bar to wake it up, it just switches off and reboots.

This is my kern.log from one of the times it worked:

```

Jun 17 22:22:45 fiona kernel: [  382.381132] wlan0: deauthenticate(reason=3)
Jun 17 22:22:45 fiona kernel: [  382.666852] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Jun 17 22:22:47 fiona kernel: [  384.779052] ACPI: PCI interrupt for device 0000:04:00.0 disabled
Jun 17 22:23:05 fiona kernel: [  385.505154] Syncing filesystems ... done.
Jun 17 22:23:05 fiona kernel: [  385.505179] PM: Preparing system for mem sleep
Jun 17 22:23:05 fiona kernel: [  385.505183] Freezing user space processes ... (elapsed 0.00 seconds) done.
Jun 17 22:23:05 fiona kernel: [  385.505758] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
Jun 17 22:23:05 fiona kernel: [  385.603211] PM: Entering mem sleep
Jun 17 22:23:05 fiona kernel: [  385.603213] Suspending console(s)
Jun 17 22:23:05 fiona kernel: [  385.605561] drm_sysfs_suspend
Jun 17 22:23:05 fiona kernel: [  385.614419] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Jun 17 22:23:05 fiona kernel: [  385.618095] sd 2:0:0:0: [sda] Stopping disk
Jun 17 22:23:05 fiona kernel: [  386.564429] ACPI handle has no context!
Jun 17 22:23:05 fiona kernel: [  386.564549] ACPI handle has no context!
Jun 17 22:23:05 fiona kernel: [  386.564572] ACPI: PCI interrupt for device 0000:0f:06.2 disabled
Jun 17 22:23:05 fiona kernel: [  386.564580] ACPI handle has no context!
Jun 17 22:23:05 fiona kernel: [  386.566726] ACPI handle has no context!
Jun 17 22:23:05 fiona kernel: [  386.567340] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Jun 17 22:23:05 fiona kernel: [  386.567649] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Jun 17 22:23:05 fiona kernel: [  386.567805] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Jun 17 22:23:05 fiona kernel: [  386.579710] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Jun 17 22:23:05 fiona kernel: [  386.579758] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Jun 17 22:23:05 fiona kernel: [  386.579806] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Jun 17 22:23:05 fiona kernel: [  386.580352] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Jun 17 22:23:05 fiona kernel: [  386.580705] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
Jun 17 22:23:05 fiona kernel: [  386.581008] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
Jun 17 22:23:05 fiona kernel: [  386.581056] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
Jun 17 22:23:05 fiona kernel: [  386.600168] Disabling non-boot CPUs ...
Jun 17 22:23:05 fiona kernel: [  386.600184] CPU0 attaching NULL sched-domain.
Jun 17 22:23:05 fiona kernel: [  386.600185] CPU1 attaching NULL sched-domain.
Jun 17 22:23:05 fiona kernel: [  386.712624] CPU 1 is now offline
Jun 17 22:23:05 fiona kernel: [  386.712627] SMP alternatives: switching to UP code
Jun 17 22:23:05 fiona kernel: [  386.713948] CPU0 attaching sched-domain:
Jun 17 22:23:05 fiona kernel: [  386.713950]  domain 0: span 01
Jun 17 22:23:05 fiona kernel: [  386.713951]   groups: 01
Jun 17 22:23:05 fiona kernel: [  386.714141] CPU1 is down
Jun 17 22:23:05 fiona kernel: [    0.181467] Back to C!

```
Waking up works just fine, so I'm skipping that. Here is what happens when it doesn't work:
```

Jun 18 07:44:25 fiona kernel: [  611.844161] wlan0: deauthenticate(reason=3)
Jun 18 07:44:25 fiona kernel: [  612.113627] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Jun 18 07:44:27 fiona kernel: [  614.225563] ACPI: PCI interrupt for device 0000:04:00.0 disabled
Jun 18 08:02:20 fiona kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jun 18 08:02:20 fiona kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Jun 18 08:02:20 fiona kernel: Symbols match kernel version 2.6.24.
Jun 18 08:02:20 fiona kernel: Loaded 19616 symbols from 100 modules.
Jun 18 08:02:20 fiona kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 18 08:02:20 fiona kernel: [    0.000000] Initializing cgroup subsys cpu
... (regular boot process continues)

```
So it just stops preparing to sleep after "ACPI: PCI interrupt for device 0000:04:00.0 disabled".

lspci gives:
```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
0f:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0f:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0f:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```
It seems like my wlan card causes the problem here:. I have tried suspending after:
- disabling networking through the network-manager
- disabling wireless through the network-manager
- physically switching off ("blocking") the wlan
- modprobe -r iwl4965

None of these measures remove the device from my lspci though (how do i do that?) and suspending still doesn't work (except once, but then it didnt work when I did the same exact thing again).

This is as far as I got on my own. Where do I go from here?

Any helpful pointers are very much appreciated.

---

