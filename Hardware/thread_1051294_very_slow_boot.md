---
title: "very slow boot"
date: 2009-01-26
forum: Hardware
---

### Post by sangmele on 2009-01-26
Hi

I tried to install Ubuntu on my Sony pcg z505ls.
it failed
i tried the alternate CD, it failed again
i finally managed to install Xubuntu, but it takes ages to boot. I loving WinXP more from day to day !

Here is data on my laptop, some excertpts from the bootlog and my bootchart.please help me !

Sony pcg z505ls
pentium III coppermine 744 MHz
248 Mb de RAM
ATI Rage Mobility (Sony)

dual boot with XP
Xubuntu 8.10 intrepid
kernel 2.6.27-9 generic

=======================================================
[    0.033997] ACPI: Checking initramfs for custom DSDT
[    0.984195] weird, boot CPU (#0) not listedby the BIOS.
[    0.984208] SMP motherboard not detected.
[    0.984218] Local APIC not detected. Using dummy APIC emulation.
[    0.984225] SMP disabled
=======================================================
[    1.571644] TCP reno registered
[    1.571999] NET: Registered protocol family 1
[    1.572464] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    2.566741]  it is
[    2.612060] Clocksource tsc unstable (delta = -2652349323 ns)
[    7.196349] Freeing initrd memory: 7999k freed
[    7.197118] Simple Boot Flag at 0x35 set to 0x1
[    7.204755] audit: initializing netlink socket (disabled)
[    7.204810] type=2000 audit(1232886821.204:1): initialized
=======================================================
[    7.336305] isapnp: Scanning for PnP cards...
[    8.720154] isapnp: No Plug & Play device found
[    9.504250] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
=======================================================
[    9.596395] Write protecting the kernel read-only data: 936k
[    9.620970] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input
1
=======================================================
[   13.072266] fuse init (API version 7.9)
[   14.330924] ACPI: CPU0 (power states: C1[C1] C2[C2])
=======================================================
[   14.368364] ACPI: Thermal Zone [ATF0] (49 C)
[   15.841902] No dock devices found.
[   16.468280] SCSI subsystem initialized
[   17.165907] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
=======================================================
[   21.025944] EXT3-fs: mounted filesystem with ordered data mode.
[   24.824239] usb-storage: device scan complete
[   24.947080] scsi 2:0:0:0: Direct-Access     Sony     MSC-U01          1.00 PQ: 0 ANSI: 0 CCS
[   25.075244] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   25.075644] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   33.899483] udevd version 124 started
[   36.669111] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
=======================================================
[   38.832128] ACPI: Power Button (CM) [PWRB]
[   41.423700] parport_pc 00:0c: reported by Plug and Play ACPI
=======================================================
[   45.716094] firmware: requesting yamaha/ds1_dsp.fw
[   48.918449] cs: IO port probe 0x100-0x3af: clean.
=======================================================
[   50.428764] firmware: requesting yamaha/ds1e_ctrl.fw
[   52.761741] loop: module loaded
=======================================================
[   58.326101] ACPI: WMI: Mapper loaded
[   59.192375] cpufreq: change to state 1 failed with new_state 2 and result 0
[   59.192375] cpufreq: change to state 0 failed with new_state 2 and result 0
[   62.560518] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
=======================================================
[   63.989695] sonypi: probe of sonypi failed with error -16
[   66.868764] ttyS2: LSR safety check engaged!
[   67.317465] Bluetooth: Core ver 2.13
=======================================================
[   67.643456] Bluetooth: SCO socket layer initialized
[  109.854765] NET: Registered protocol family 10
=======================================================
[  109.870168] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  182.412270] ppdev0: registered pardevice
=======================================================
[  185.036780] ppdev0: unregistered pardevice
[  230.784069] usb 1-2: new full speed USB device using uhci_hcd and address 4

[[IMG]http://img502.imageshack.us/img502/7578/intrepid200901261dv7.png[/IMG]](http://img502.imageshack.us/my.php?image=intrepid200901261dv7.png)
[[IMG]http://img502.imageshack.us/img502/intrepid200901261dv7.png/1/w294.png[/IMG]](http://g.imageshack.us/img502/intrepid200901261dv7.png/1/)

---

