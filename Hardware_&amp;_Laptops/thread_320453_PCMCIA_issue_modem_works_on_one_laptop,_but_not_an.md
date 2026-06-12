---
title: "PCMCIA issue: modem works on one laptop, but not another."
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by daller on 2006-12-17
Hi there,

I've tried to get my **Option Globetrotter 3G Quad** card running, but there seems to be something wrong.

I've tried on 2 laptops:

Dell Inspiron 8600: 

```
daniel@dallap:~$ sudo tail -f /var/log/syslog 

Dec 17 16:18:12 dallap kernel: [17180945.652000] pccard: CardBus card inserted into slot 0
Dec 17 16:18:12 dallap kernel: [17180945.652000] PCI: device 0000:03:00.0 has unknown header type 7f, ignoring.
```

Acer Travelmate 290:

```
Nov 19 13:22:04 localhost kernel: [17179828.256000] pccard: CardBus card inserted into slot 0
Nov 19 13:22:04 localhost kernel: [17179828.256000] yenta EnE: chaning testregister 0xC9, 04 -> 04
Nov 19 13:22:04 localhost NetworkManager: <debug info>^I[1163938924.453689] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1033_35').
Nov 19 13:22:04 localhost NetworkManager: <debug info>^I[1163938924.567560] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1033_35_0').
Nov 19 13:22:04 localhost kernel: [17179828.432000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
Nov 19 13:22:04 localhost kernel: [17179828.432000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Nov 19 13:22:04 localhost kernel: [17179828.432000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov 19 13:22:04 localhost kernel: [17179828.432000] PCI: Setting latency timer of device 0000:02:00.0 to 64
Nov 19 13:22:04 localhost kernel: [17179828.432000] ohci_hcd 0000:02:00.0: OHCI Host Controller
Nov 19 13:22:04 localhost kernel: [17179828.432000] ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 5
Nov 19 13:22:04 localhost kernel: [17179828.432000] ohci_hcd 0000:02:00.0: irq 10, io mem 0xe2000000
Nov 19 13:22:04 localhost kernel: [17179828.516000] usb usb5: configuration #1 chosen from 1 choice
Nov 19 13:22:04 localhost kernel: [17179828.516000] hub 5-0:1.0: USB hub found
Nov 19 13:22:04 localhost kernel: [17179828.516000] hub 5-0:1.0: 1 port detected
Nov 19 13:22:04 localhost kernel: [17179828.620000] PCI: Enabling device 0000:02:00.1 (0000 -> 0002)
Nov 19 13:22:04 localhost kernel: [17179828.620000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov 19 13:22:04 localhost kernel: [17179828.620000] PCI: Setting latency timer of device 0000:02:00.1 to 64
Nov 19 13:22:04 localhost kernel: [17179828.620000] ohci_hcd 0000:02:00.1: OHCI Host Controller
Nov 19 13:22:04 localhost kernel: [17179828.620000] ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 6
Nov 19 13:22:04 localhost kernel: [17179828.620000] ohci_hcd 0000:02:00.1: irq 10, io mem 0xe2001000
Nov 19 13:22:04 localhost kernel: [17179828.708000] usb usb6: configuration #1 chosen from 1 choice
Nov 19 13:22:04 localhost kernel: [17179828.708000] hub 6-0:1.0: USB hub found
Nov 19 13:22:04 localhost kernel: [17179828.708000] hub 6-0:1.0: 1 port detected
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.006258] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1').
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.065330] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0').
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.110200] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1_if0').
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.172053] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0_if0').
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.250977] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0_usbraw').
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.296604] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1_usbraw').
Nov 19 13:22:07 localhost kernel: [17179831.068000] ohci_hcd 0000:02:00.1: wakeup
Nov 19 13:22:07 localhost kernel: [17179831.452000] usb 6-1: new full speed USB device using ohci_hcd and address 2
Nov 19 13:22:07 localhost kernel: [17179831.664000] usb 6-1: configuration #1 chosen from 1 choice
Nov 19 13:22:07 localhost NetworkManager: <debug info>^I[1163938927.861818] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe').
Nov 19 13:22:07 localhost NetworkManager: <debug info>^I[1163938927.909043] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if0').
Nov 19 13:22:07 localhost NetworkManager: <debug info>^I[1163938927.968372] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if1').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.012860] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if2').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.078164] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if3').
Nov 19 13:22:08 localhost kernel: [17179832.012000] usbcore: registered new driver usbserial
Nov 19 13:22:08 localhost kernel: [17179832.012000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Nov 19 13:22:08 localhost kernel: [17179832.012000] usbcore: registered new driver usbserial_generic
Nov 19 13:22:08 localhost kernel: [17179832.012000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
Nov 19 13:22:08 localhost kernel: [17179832.016000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Option 3G data card
Nov 19 13:22:08 localhost kernel: [17179832.016000] option 6-1:1.0: Option 3G data card converter detected
Nov 19 13:22:08 localhost kernel: [17179832.020000] usb 6-1: Option 3G data card converter now attached to ttyUSB0
Nov 19 13:22:08 localhost kernel: [17179832.020000] option 6-1:1.1: Option 3G data card converter detected
Nov 19 13:22:08 localhost kernel: [17179832.020000] usb 6-1: Option 3G data card converter now attached to ttyUSB1
Nov 19 13:22:08 localhost kernel: [17179832.020000] option 6-1:1.2: Option 3G data card converter detected
Nov 19 13:22:08 localhost kernel: [17179832.020000] usb 6-1: Option 3G data card converter now attached to ttyUSB2
Nov 19 13:22:08 localhost kernel: [17179832.020000] option 6-1:1.3: Option 3G data card converter detected
Nov 19 13:22:08 localhost kernel: [17179832.020000] usb 6-1: Option 3G data card converter now attached to ttyUSB3
Nov 19 13:22:08 localhost kernel: [17179832.020000] usbcore: registered new driver option
Nov 19 13:22:08 localhost kernel: [17179832.020000] drivers/usb/serial/option.c: Option Card (PC-Card to) USB to Serial Driver: v0.4
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.194435] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if2_serial_usb_2').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.218645] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if0_serial_usb_0').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.242503] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if3_serial_usb_3').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.281788] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_usbraw').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.305524] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if1_serial_usb_1').
```

Another thing (which may explaing things?) is that **cardctl** package is not installed on the Dell...

After following this: [https://help.ubuntu.com/community/forum/hardware/Option3gCard](https://help.ubuntu.com/community/forum/hardware/Option3gCard) I got everything running on the Acer, but the Dell is still not doing anything at all with the card.

TIA!

---

