---
title: "Wavecom GSM USB Module"
date: 2010-11-21
forum: Hardware
---

### Post by naes on 2010-11-21
Recently I acquired a Wavecom GSM (dual band) USB based module to allow me to send SMS alerts.

Connected the device is correctly assigned to /dev/ttyUSB0 see dmesg output

```

[13099.768212] usb 5-2: new full speed USB device using uhci_hcd and address 3
[13099.927801] usb 5-2: configuration #1 chosen from 1 choice
[13099.981181] usbcore: registered new interface driver usbserial
[13099.981579] USB Serial support registered for generic
[13099.981710] usbcore: registered new interface driver usbserial_generic
[13099.981714] usbserial: USB Serial Driver core
[13099.991830] USB Serial support registered for pl2303
[13099.992950] pl2303 5-2:1.0: pl2303 converter detected
[13100.004843] usb 5-2: pl2303 converter now attached to ttyUSB0
[13100.004876] usbcore: registered new interface driver pl2303
[13100.004880] pl2303: Prolific PL2303 USB to serial adaptor driver
```

When connecting to said device via minicom despite using the correct device & baud settings I keep getting garbled output (see screenshot)

---

