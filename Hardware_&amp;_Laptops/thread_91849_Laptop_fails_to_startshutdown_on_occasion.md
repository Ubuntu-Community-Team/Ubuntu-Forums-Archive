---
title: "Laptop fails to start/shutdown on occasion"
date: 2005-11-18
forum: Hardware &amp; Laptops
---

### Post by markr on 2005-11-18
My laptop is a Dell Inspiron 5150.
Kernel : 2.6.12-9-386 (from install CD)
Kernel options are : ro quiet splash

This problem occurs in Ubuntu and Kubuntu;  I'm currently running KUbuntu.

On occasion (problem every 3-5 reboots),  my laptop will startup (or shutdown,  but I'll cover startup only as I think it's the same problem) and then just hang with a blank screen,  a hard reboot is the only way to recover from this.

**When it fails to start,  the log ends like this :**

Nov 18 08:36:35 localhost kernel: [4294705.853000]   options:  [pci] [cardbus] [pm]
Nov 18 08:36:35 localhost kernel: [4294705.865000] PCI: Enabling device 0000:02:04.0 (0000 -> 0002)
Nov 18 08:36:35 localhost kernel: [4294705.865000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov 18 08:36:35 localhost kernel: [4294705.865000] Yenta: CardBus bridge found at 0000:02:04.0 [1028:015f]
Nov 18 08:36:35 localhost kernel: [4294705.865000] Yenta: Using CSCINT to route CSC interrupts to PCI
Nov 18 08:36:35 localhost kernel: [4294705.865000] Yenta: Routing CardBus interrupts to PCI
Nov 18 08:36:35 localhost kernel: [4294705.865000] Yenta TI: socket 0000:02:04.0, mfunc 0x00001002, devctl 0x64
Nov 18 08:36:35 localhost kernel: [4294706.086000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
Nov 18 08:36:35 localhost kernel: [4294706.086000] Socket status: 30000020
Nov 18 08:36:35 localhost kernel: [4294706.182000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
Nov 18 08:36:35 localhost kernel: [4294706.182000] ACPI: PCI Interrupt 0000:02:04.1[A] -> GSI 16 (level, low) -> IRQ 16
Nov 18 08:36:35 localhost kernel: [4294706.237000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]
Nov 18 08:36:35 localhost kernel: [4294706.778000] ndiswrapper: driver bcmwl5 (Broadcom,07/17/2003, 3.30.15.0) loaded
Nov 18 08:36:35 localhost kernel: [4294706.779000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Nov 18 08:36:35 localhost kernel: [4294706.779000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov 18 08:36:35 localhost kernel: [4294706.784000] ndiswrapper: using irq 16
Nov 18 08:36:35 localhost kernel: [4294707.442000] wlan0: ndiswrapper ethernet device 00:11:50:0c:df:63 using driver bcmwl5, configuration file 14E4:4320.5.conf
Nov 18 08:36:35 localhost kernel: [4294707.442000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
Nov 18 08:36:35 localhost kernel: [4294708.077000] Real Time Clock Driver v1.12
Nov 18 08:36:35 localhost kernel: [4294708.155000] input: PC Speaker
Nov 18 08:36:35 localhost kernel: [4294710.766000] ACPI: AC Adapter [AC] (on-line)
Nov 18 08:36:35 localhost kernel: [4294711.066000] ACPI: Battery Slot [BAT0] (battery present)
Nov 18 08:36:35 localhost kernel: [4294711.080000] ACPI: Lid Switch [LID]
Nov 18 08:36:35 localhost kernel: [4294711.080000] ACPI: Power Button (CM) [PBTN]
Nov 18 08:36:35 localhost kernel: [4294711.080000] ACPI: Sleep Button (CM) [SBTN]
Nov 18 08:36:35 localhost kernel: [4294711.277000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Nov 18 08:36:37 localhost hp: unable to open /var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 75
Nov 18 08:36:37 localhost hpiod: 0.9.5 accepting connections at 32770...

**For a successful boot,  the log is exactly the same as above, but then continues with :**

Nov 18 08:41:57 localhost kernel: [4294713.692000] apm: BIOS not found.
Nov 18 08:41:58 localhost kernel: [4294714.418000] cs: IO port probe 0x100-0x4ff: clean.
Nov 18 08:41:58 localhost kernel: [4294714.420000] cs: IO port probe 0xc00-0xcf7: clean.
Nov 18 08:41:58 localhost kernel: [4294714.420000] cs: IO port probe 0xa00-0xaff: clean.
Nov 18 08:41:58 localhost kernel: [4294715.210000] Bluetooth: Core ver 2.7
Nov 18 08:41:58 localhost kernel: [4294715.210000] NET: Registered protocol family 31
Nov 18 08:41:58 localhost kernel: [4294715.210000] Bluetooth: HCI device and connection manager initialized
Nov 18 08:41:58 localhost kernel: [4294715.210000] Bluetooth: HCI socket layer initialized
Nov 18 08:41:58 localhost kernel: [4294715.269000] Bluetooth: L2CAP ver 2.7
Nov 18 08:41:58 localhost kernel: [4294715.269000] Bluetooth: L2CAP socket layer initialized
Nov 18 08:41:58 localhost kernel: [4294715.310000] Bluetooth: RFCOMM ver 1.5
Nov 18 08:41:58 localhost kernel: [4294715.310000] Bluetooth: RFCOMM socket layer initialized
Nov 18 08:41:58 localhost kernel: [4294715.310000] Bluetooth: RFCOMM TTY layer initialized
Nov 18 08:42:01 localhost kernel: [4294717.523000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Nov 18 08:42:01 localhost kernel: [4294717.523000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Nov 18 08:42:01 localhost kernel: [4294717.523000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Nov 18 08:42:01 localhost kernel: [4294718.095000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Nov 18 08:42:01 localhost kernel: [4294718.095000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Nov 18 08:42:01 localhost kernel: [4294718.095000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Nov 18 08:42:15 localhost ivman: Ivman started in system mode
Nov 18 08:47:36 localhost exiting on signal 15
Nov 18 08:47:37 localhost syslogd 1.4.1#17ubuntu3: restart.
Nov 18 09:07:37 localhost -- MARK --

Any thoughts most welcome!!!

---

### Post by markr on 2005-11-21
Bump

Any help at all?

Thanks

Mark.

---

### Post by SwePete on 2005-12-07
Have you tried without the splash option ? I saw som sugestion on that to help out on some shutdown reboot problems.

---

### Post by zonk on 2005-12-07
[QUOTE=SwePete]Have you tried without the splash option ? I saw som sugestion on that to help out on some shutdown reboot problems.[/QUOTE]

Hi SwePete. I had some problems of shutingdown my laptop(lg lw 40 ) and exactly the turning of the splash option solved it. I had never heard of that before. 
Even if it doesn't help markr this thread was worth existing ;)

Thanks

zonk

---

