---
title: "Keyboard problems"
date: 2010-07-25
forum: Hardware
---

### Post by fiftyhillswest on 2010-07-25
Hello,

I'm experiencing some problems with my USB keyboard (Logitech UltraX Premium). Every time I power up my computer and get into ubuntu, it won't respond to any keyboard input. The only solution I've found so far is replugging my keyboard, but I wouldn't call that a solution.

**Other solutions I've tried which should work**:
- Enable USB Legacy support in BIOS:
    * Was already enabled, didn't work.

- Disable ACPI completely:
    * Worked one time only, after that it still wouldn't take any keyboard input.

- Boot-up script called usbfix.sh which removes the ohci_hcd module and probes it again:
    * No luck. 

**Other information**:
Ubuntu 10.04 x86_64
Does respond to USB mouse somehow...

**Relevant hardware**:
- Logitech UltraX Premium USB keyboard
- Logitech MX518 USB mouse
- Motherboard: MSI K9N Neo-F with nVidia MCP55 USB Controller

**uname -a**:
```
Linux maarten-desktop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux
```**dmesg | grep usb** (after replugging):
```

[    0.352803] usbcore: registered new interface driver usbfs
[    0.352819] usbcore: registered new interface driver hub
[    0.352850] usbcore: registered new device driver usb
[    0.950123] usb usb1: configuration #1 chosen from 1 choice
[    1.012100] usb usb2: configuration #1 chosen from 1 choice
[    1.610028] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    1.838145] usb 2-1: configuration #1 chosen from 1 choice
[    2.180026] usb 2-3: new low speed USB device using ohci_hcd and address 3
[    2.418039] usb 2-3: config index 0 descriptor too short (expected 59, got 43)
[    2.418042] usb 2-3: config 1 has an invalid descriptor of length 107, skipping remainder of the config
[    2.418046] usb 2-3: config 1 has 1 interface, different from the descriptor's value: 2
[    2.437139] usb 2-3: configuration #1 chosen from 1 choice
[    2.446651] usbcore: registered new interface driver hiddev
[    2.453396] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
[    2.453515] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-1/input0
[    2.477315] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input4
[    2.477385] generic-usb 0003:046D:C30E.0002: input,hidraw1: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:00:02.0-3/input0
[    2.477410] usbcore: registered new interface driver usbhid
[    2.477413] usbhid: v2.6:USB HID core driver
[   36.943787] usb 2-3: USB disconnect, address 3
[   39.560027] usb 2-2: new low speed USB device using ohci_hcd and address 4
[   39.808093] usb 2-2: configuration #1 chosen from 1 choice
[   39.826337] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input6
[   39.826459] generic-usb 0003:046D:C30E.0003: input,hidraw1: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:00:02.0-2/input0
[   39.853057] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input7
[   39.853185] generic-usb 0003:046D:C30E.0004: input,hidraw2: USB HID v1.10 Device [Logitech HID compliant keyboard] on usb-0000:00:02.0-2/input1
[  682.511256] usb 2-2: USB disconnect, address 4
[  682.990054] usb 2-2: new low speed USB device using ohci_hcd and address 5
[  683.237449] usb 2-2: configuration #1 chosen from 1 choice
[  683.254717] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input8
[  683.254846] generic-usb 0003:046D:C30E.0005: input,hidraw1: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:00:02.0-2/input0
[  683.281447] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input9
[  683.281577] generic-usb 0003:046D:C30E.0006: input,hidraw2: USB HID v1.10 Device [Logitech HID compliant keyboard] on usb-0000:00:02.0-2/input1

```Does anyone have an idea how to fix this or other things I could try?

---

