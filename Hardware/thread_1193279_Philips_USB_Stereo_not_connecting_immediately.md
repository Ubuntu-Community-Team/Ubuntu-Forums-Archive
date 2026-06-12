---
title: "Philips USB Stereo not connecting immediately"
date: 2009-06-21
forum: Hardware
---

### Post by CHW on 2009-06-21
Hello,

On my Dell notebook I use a Philips USB stereo to listen to some music.
When I plug in the device it is mostly not recognised immediately, I have to re-plug it several times until Ubuntu (9.04) recognises it.
Then everything works fine.

This problem is an old one, it was already before Ubuntu 9.04.

Here are some log files. At the end of each log the device is always working.

syslog:
```
Jun 21 15:02:06 laptop kernel: [ 3026.824303] hub 2-0:1.0: unable to enumerate USB device on port 3
Jun 21 15:02:08 laptop kernel: [ 3028.521264] usb 6-1: new full speed USB device using uhci_hcd and address 3
Jun 21 15:02:08 laptop kernel: [ 3029.048191] usb 6-1: device not accepting address 3, error -71
Jun 21 15:02:08 laptop kernel: [ 3029.104226] hub 6-0:1.0: unable to enumerate USB device on port 1
Jun 21 15:02:57 laptop kernel: [ 3077.344175] usb 6-1: new full speed USB device using uhci_hcd and address 5
Jun 21 15:02:57 laptop kernel: [ 3077.530957] usb 6-1: configuration #1 chosen from 1 choice
Jun 21 15:02:57 laptop kernel: [ 3077.619647] input: Philips UAC3553B as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.2/input/input9
Jun 21 15:02:57 laptop kernel: [ 3077.632355] generic-usb 0003:0471:0110.0002: input,hidraw1: USB HID v1.00 Device [Philips UAC3553B] on usb-0000:00:1d.1-1/input2
Jun 21 15:02:57 laptop kernel: [ 3077.854308] usbcore: registered new interface driver snd-usb-audio
```

```
Jun 21 16:04:16 laptop kernel: [ 6756.672189] usb 6-1: new full speed USB device using uhci_hcd and address 8
Jun 21 16:04:16 laptop kernel: [ 6756.736789] hub 6-0:1.0: unable to enumerate USB device on port 1
Jun 21 16:04:26 laptop kernel: [ 6766.840178] usb 6-1: new full speed USB device using uhci_hcd and address 9
Jun 21 16:04:26 laptop kernel: [ 6766.904263] hub 6-0:1.0: unable to enumerate USB device on port 1
Jun 21 16:04:29 laptop kernel: [ 6769.569160] usb 6-1: new full speed USB device using uhci_hcd and address 10
Jun 21 16:04:29 laptop kernel: [ 6769.761813] usb 6-1: configuration #1 chosen from 1 choice
Jun 21 16:04:29 laptop kernel: [ 6769.879165] input: Philips UAC3553B as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.2/input/input12
Jun 21 16:04:29 laptop kernel: [ 6769.904361] generic-usb 0003:0471:0110.0005: input,hidraw1: USB HID v1.00 Device [Philips UAC3553B] on usb-0000:00:1d.1-1/input2
```

```
Jun 21 16:13:42 laptop kernel: [ 7322.608209] usb 6-1: new full speed USB device using uhci_hcd and address 16
Jun 21 16:13:42 laptop kernel: [ 7322.804062] usb 6-1: configuration #1 chosen from 1 choice
Jun 21 16:13:42 laptop kernel: [ 7322.900236] input: Philips UAC3553B as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.2/input/input14
Jun 21 16:13:42 laptop kernel: [ 7322.932666] generic-usb 0003:0471:0110.0008: input,hidraw1: USB HID v1.00 Device [Philips UAC3553B] on usb-0000:00:1d.1-1/input2
Jun 21 16:13:59 laptop kernel: [ 7339.441090] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.737125] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.738105] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.739127] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.740152] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.742131] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.743093] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.744151] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.746125] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.747092] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.748146] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.750089] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.751104] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.752074] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.753089] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.754110] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.756079] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.757156] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.759422] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.760079] 16:1:1: usb_set_interface failed
Jun 21 16:14:00 laptop kernel: [ 7340.761074] 16:1:1: usb_set_interface failed
Jun 21 16:14:04 laptop kernel: [ 7344.440226] usb 6-1: USB disconnect, address 16
Jun 21 16:14:11 laptop kernel: [ 7351.816222] hub 6-0:1.0: unable to enumerate USB device on port 1
Jun 21 16:14:15 laptop kernel: [ 7355.840366] usb 6-1: new full speed USB device using uhci_hcd and address 18
Jun 21 16:14:15 laptop kernel: [ 7356.037084] usb 6-1: configuration #1 chosen from 1 choice
Jun 21 16:14:15 laptop kernel: [ 7356.130288] input: Philips UAC3553B as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.2/input/input15
Jun 21 16:14:15 laptop kernel: [ 7356.160229] generic-usb 0003:0471:0110.0009: input,hidraw1: USB HID v1.00 Device [Philips UAC3553B] on usb-0000:00:1d.1-1/input2
```

Xorg.0.log:
```
(II) config/hal: Adding input device Philips UAC3553B
(**) Philips UAC3553B: always reports core events
(**) Philips UAC3553B: Device: "/dev/input/event9"
(II) Philips UAC3553B: Found keys
(II) Philips UAC3553B: Configuring as keyboard
(II) XINPUT: Adding extended input device "Philips UAC3553B" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Philips UAC3553B: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Philips UAC3553B: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) Philips UAC3553B: xkb_layout: "de"
```

I would appreciate any help.
When I have to provide other outputs, please tell me.

Regards,
CHW

---

### Post by CHW on 2009-06-24
Bump

---

