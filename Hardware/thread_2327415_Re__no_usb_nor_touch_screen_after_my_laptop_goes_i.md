---
title: "Re:  no usb nor touch screen after my laptop goes into sleep"
date: 2016-06-10
forum: Hardware
---

### Post by frlaurent on 2016-06-10
Dear you all,
I am back to ubuntu after some time.
I made an ubuntu 16.04 fresh install  on LENOVO S20 30 Touch.
It ran like charm until computer goes into sleep.
Logging back
----> no usb (either usb2 or usb3) plugged can be mounted ; nothing in dmesg neither fdisk.
----> touch screen doesn't work anymore.

Any idea ?

thank you
Larry

I ended up getting dmesg output :

```
[    0.008000] ACPI: Waking up from system sleep state S3
[    0.008000] clocksource: Switched to clocksource acpi_pm
[  668.048525] acpi LNXPOWER:02: Turning OFF
[  668.048663] acpi LNXPOWER:01: Turning OFF
[  668.048765] acpi LNXPOWER:00: Turning OFF
[  668.064626] pci_raw_set_power_state: 33 callbacks suppressed
[  668.064636] sdhci-pci 0000:00:17.0: Refused to change power state, currently in D3
[  668.124333] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
[  668.124658] PM: noirq resume of devices complete after 75.867 msecs
[  668.197409] PM: early resume of devices complete after 72.694 msecs
[  668.218182] xhci_hcd 0000:00:14.0: WARNING: Host System Error
[  668.218188] xhci_hcd 0000:00:14.0: WARNING: Host System Error
[  668.237225] r8169 0000:01:00.0: System wakeup disabled by ACPI
[  668.317299] mmc1: Reset 0x1 never completed.
[  668.317398] rtlwifi: rtlwifi: wireless switch is on
[  668.344033] xhci_hcd 0000:00:14.0: port 1 resume PLC timeout
[  668.363963] sd 0:0:0:0: [sda] Starting disk
[  668.365158] mmc0: Reset 0x1 never completed.
[  668.367272] r8169 0000:01:00.0 enp1s0: link down
[  668.367507] rtc_cmos 00:00: System wakeup disabled by ACPI
[  668.580255] usb 1-2: reset full-speed USB device number 2 using xhci_hcd
[  668.652736] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  668.666716] ata1.00: configured for UDMA/133
[  668.692224] usb 1-2: device descriptor read/64, error -22
[  668.908258] usb 1-2: device descriptor read/64, error -22
[  669.124167] usb 1-2: reset full-speed USB device number 2 using xhci_hcd
[  669.236109] usb 1-2: device descriptor read/64, error -22
[  669.452206] usb 1-2: device descriptor read/64, error -22
[  669.668185] usb 1-2: reset full-speed USB device number 2 using xhci_hcd
[  669.684189] usb 1-2: device descriptor read/8, error -22
[  669.724833] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x350f00)
[  669.744529] psmouse serio1: elantech: Synaptics capabilities query result 0x48, 0x17, 0x0b.
[  669.762873] psmouse serio1: elantech: Elan sample query result 00, 67, 95
[  669.804260] usb 1-2: device descriptor read/8, error -22
[  669.864292] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input16
[  670.020186] usb 1-2: reset full-speed USB device number 2 using xhci_hcd
[  670.036185] usb 1-2: device descriptor read/8, error -22
[  670.156183] usb 1-2: device descriptor read/8, error -22
[  670.260879] PM: resume of devices complete after 2063.463 msecs
[  670.261377] PM: Finishing wakeup.
[  670.261381] Restarting tasks ... done.
[  670.291511] usb 1-2: USB disconnect, device number 2
[  670.320689] usb usb1-port2: couldn't allocate usb_device
[  670.320759] usb 1-3: USB disconnect, device number 3
[  670.356580] usb usb1-port3: couldn't allocate usb_device
[  670.356726] usb 1-4: USB disconnect, device number 4
[  670.356732] usb 1-4.2: USB disconnect, device number 5
[  670.366767] usb 1-4.4: USB disconnect, device number 6
[  670.508441] usb usb1-port4: couldn't allocate usb_device
[  670.690318] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[  670.706121] r8169 0000:01:00.0 enp1s0: link down
[  670.706245] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[  670.707538] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  671.423130] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  671.549884] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  673.500364] r8169 0000:01:00.0 enp1s0: link up
[  673.500380] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
```

---

### Post by sasseones on 2016-06-11
Is this Ubuntu install on a 32bit UEFI computer? I have had problems with touch screen and sleep on 32 UEFI computers.

---

### Post by frlaurent on 2016-06-12
Yeap, but 64 UEFI.
BTW I switch to Legacy support before installation. and boot priority is set to Legacy first :
[IMG][[IMG]http://s33.postimg.org/c8a5yhibv/UEFI.jpg[/IMG]]("http://postimg.org/image/c8a5yhibv/")[/IMG]

---

