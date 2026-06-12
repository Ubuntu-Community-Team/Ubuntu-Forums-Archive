---
title: "[ask] USB drive not recognized"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by anak_design on 2006-12-11
I have search through out the forums, but there's seem no definite solution to this one problem. One post even mentioned that Ubuntu 6.10 is having an issue with mounting USB drive?

My case is that whenever I plug my USB drive to my USB (Im using laptop btw), it doesn't auto mount, and I doubt it even recognized. Any idea why? I've tried to install usbautomount package, but it does not make any difference. What should I do?

Thank you.

p/s: When I plug a mouse to the same USB port, it works.. so this means that the USB port has no problem right?

---

### Post by pandu.rs on 2006-12-11
u need to run the following command (after inserting ur device into usb port) to check if ur device is detected.

dmesg | tail -50

if u could paste the output here.. it might be helpful

---

### Post by anak_design on 2006-12-11
Here's what I got:

[17179596.892000] ACPI: Power Button (FF) [PWRF]
[17179596.892000] ACPI: Lid Switch [LID]
[17179596.892000] ACPI: Power Button (CM) [PWRB]
[17179597.064000] ibm_acpi: ec object not found
[17179597.096000] pcc_acpi: loading...
[17179597.492000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179597.492000] acpi-cpufreq: CPU1 - ACPI performance management activated.
[17179601.912000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179601.912000] apm: disabled - APM is not SMP safe.
[17179602.676000] [drm] Initialized drm 1.0.1 20051102
[17179602.688000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179602.688000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179603.832000] mtrr: 0xa0000000,0x8000000 overlaps existing 0xa0000000,0x4000000
[17179603.836000] mtrr: 0xa0000000,0x8000000 overlaps existing 0xa0000000,0x4000000
[17179603.836000] mtrr: 0xa0000000,0x8000000 overlaps existing 0xa0000000,0x4000000
[17179603.836000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179603.836000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179603.836000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[17179604.024000] [drm] Setting GART location based on new memory map
[17179604.024000] [drm] writeback test succeeded in 1 usecs
[17179605.196000] NET: Registered protocol family 10
[17179605.196000] lo: Disabled Privacy Extensions
[17179605.200000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179605.200000] IPv6 over IPv4 tunneling driver
[17179606.676000] Bluetooth: Core ver 2.8
[17179606.676000] NET: Registered protocol family 31
[17179606.676000] Bluetooth: HCI device and connection manager initialized
[17179606.676000] Bluetooth: HCI socket layer initialized
[17179606.716000] Bluetooth: L2CAP ver 2.8
[17179606.716000] Bluetooth: L2CAP socket layer initialized
[17179606.768000] Bluetooth: RFCOMM socket layer initialized
[17179606.768000] Bluetooth: RFCOMM TTY layer initialized
[17179606.768000] Bluetooth: RFCOMM ver 1.7
[17179615.400000] ath0: no IPv6 routers present
[17184202.988000] hub 3-0:1.0: over-current change on port 2
[17184203.424000] ohci_hcd 0000:00:13.0: wakeup
[17184203.808000] usb 1-3: new full speed USB device using ohci_hcd and address 2
[17184204.028000] usb 1-3: configuration #1 chosen from 1 choice
[17184204.172000] usbcore: registered new driver libusual
[17184204.196000] Initializing USB Mass Storage driver...
[17184204.196000] scsi0 : SCSI emulation for USB Mass Storage devices
[17184204.200000] usbcore: registered new driver usb-storage
[17184204.200000] USB Mass Storage support registered.
[17184204.200000] usb-storage: device found at 2
[17184204.200000] usb-storage: waiting for device to settle before scanning
[17184209.200000] usb-storage: device scan complete
[17184209.380000] usb 1-3: reset full speed USB device using ohci_hcd and address 2
[17184209.768000] usb 1-3: reset full speed USB device using ohci_hcd and address 2
[17184210.156000] usb 1-3: reset full speed USB device using ohci_hcd and address 2
[17184210.544000] usb 1-3: reset full speed USB device using ohci_hcd and address 2

---

### Post by pandu.rs on 2006-12-11
Ok. 
Go to system->preferences->removable drives and media

check in the storage tab, if u have first 3 check boxes checked. i am also attaching screenshot in my computer.

---

### Post by pandu.rs on 2006-12-11
> **pandu.rs said:**
> Ok. 
Go to system->preferences->removable drives and media

check in the storage tab, if u have first 3 check boxes checked. i am also attaching screenshot in my computer.

screenshot attached now

---

### Post by anak_design on 2006-12-11
yep, got that checked.. but still, my USB is not mounted...](*,)

---

### Post by pandu.rs on 2006-12-12
here is a thread one of my friend provided me.

[http://linuxgazette.net/133/tag.html](http://linuxgazette.net/133/tag.html)

---

### Post by joe.webster on 2006-12-16
I had a similar problem and fixed it.

[http://www.ubuntuforums.org/showthread.php?t=319897]("http://www.ubuntuforums.org/showthread.php?t=319897")

---

