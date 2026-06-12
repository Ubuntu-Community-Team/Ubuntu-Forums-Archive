---
title: "USB Headset doesnt show up in lsusb"
date: 2015-09-08
forum: Hardware
---

### Post by nillerzen on 2015-09-08
Hello, i have a razer megalodon 7.1 usb headset that i have been using for years, and also sometimes under linux.

i have kept turning away from linux but decided to give it another go.

I then ran into a problem i have had in the past, my usb headset doesnt show up under the page where i can choose it as a sound output.
the fix in the past has been to restart the pc with the usb plugged out, and plug it in when i was booted in.

this did not work this time.

the wierd thing is, as ubuntu was installing i was watching a youtube video trough the live usb with sound no problem. 

it doesnt look like lsusb can find the device
```

Bus 006 Device 002: ID 8087:8001 Intel Corp. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1532:0043 Razer USA, Ltd 
Bus 003 Device 002: ID 1532:010b Razer USA, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 8087:8009 Intel Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 174c:3074 ASMedia Technology Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

dmesg | grep usb gives me this output

```
[    0.234518] usbcore: registered new interface driver usbfs
[    0.234522] usbcore: registered new interface driver hub
[    0.234533] usbcore: registered new device driver usb
[    0.452951] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.452952] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.452953] usb usb1: Product: xHCI Host Controller
[    0.452954] usb usb1: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
[    0.452955] usb usb1: SerialNumber: 0000:00:14.0
[    0.455670] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.455670] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.455671] usb usb2: Product: xHCI Host Controller
[    0.455672] usb usb2: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
[    0.455673] usb usb2: SerialNumber: 0000:00:14.0
[    0.517580] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.517581] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.517581] usb usb3: Product: xHCI Host Controller
[    0.517582] usb usb3: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
[    0.517583] usb usb3: SerialNumber: 0000:05:00.0
[    0.517755] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.517756] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.517756] usb usb4: Product: xHCI Host Controller
[    0.517757] usb usb4: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
[    0.517758] usb usb4: SerialNumber: 0000:05:00.0
[    0.533765] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    0.533766] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.533767] usb usb5: Product: EHCI Host Controller
[    0.533767] usb usb5: Manufacturer: Linux 3.19.0-28-generic ehci_hcd
[    0.533768] usb usb5: SerialNumber: 0000:00:1a.0
[    0.549771] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
[    0.549771] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.549772] usb usb6: Product: EHCI Host Controller
[    0.549773] usb usb6: Manufacturer: Linux 3.19.0-28-generic ehci_hcd
[    0.549774] usb usb6: SerialNumber: 0000:00:1d.0
[    0.765788] usb 1-3: new high-speed USB device number 2 using xhci_hcd
[    0.765965] usb 2-3: new SuperSpeed USB device number 2 using xhci_hcd
[    0.783437] usb 2-3: New USB device found, idVendor=174c, idProduct=3074
[    0.783439] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=0
[    0.783449] usb 2-3: Product: ASM107x
[    0.783449] usb 2-3: Manufacturer: Asmedia
[    0.845787] usb 5-1: new high-speed USB device number 2 using ehci-pci
[    0.861789] usb 6-1: new high-speed USB device number 2 using ehci-pci
[    0.881786] usb 3-1: new full-speed USB device number 2 using xhci_hcd
[    0.978121] usb 5-1: New USB device found, idVendor=8087, idProduct=8009
[    0.978122] usb 5-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.994140] usb 6-1: New USB device found, idVendor=8087, idProduct=8001
[    0.994142] usb 6-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.177331] usb 3-1: New USB device found, idVendor=1532, idProduct=010b
[    1.177333] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.177334] usb 3-1: Product: Razer Arctosa
[    1.177334] usb 3-1: Manufacturer: Razer
[    1.177446] usb 3-1: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.184771] usbcore: registered new interface driver usbhid
[    1.184772] usbhid: USB HID core driver
[    1.185532] input: Razer Razer Arctosa as /devices/pci0000:00/0000:00:1c.4/0000:05:00.0/usb3/3-1/3-1:1.0/0003:1532:010B.0001/input/input6
[    1.241833] hid-generic 0003:1532:010B.0001: input,hidraw0: USB HID v1.11 Keyboard [Razer Razer Arctosa] on usb-0000:05:00.0-1/input0
[    1.242332] input: Razer Razer Arctosa as /devices/pci0000:00/0000:00:1c.4/0000:05:00.0/usb3/3-1/3-1:1.1/0003:1532:010B.0002/input/input7
[    1.297862] hid-generic 0003:1532:010B.0002: input,hidraw1: USB HID v1.11 Device [Razer Razer Arctosa] on usb-0000:05:00.0-1/input1
[    1.345770] usb 3-2: new full-speed USB device number 3 using xhci_hcd
[    1.639278] usb 3-2: New USB device found, idVendor=1532, idProduct=0043
[    1.639280] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.639281] usb 3-2: Product: Razer DeathAdder Chroma
[    1.639281] usb 3-2: Manufacturer: Razer
[    1.642318] input: Razer Razer DeathAdder Chroma as /devices/pci0000:00/0000:00:1c.4/0000:05:00.0/usb3/3-2/3-2:1.0/0003:1532:0043.0003/input/input8
[    1.642569] hid-generic 0003:1532:0043.0003: input,hidraw2: USB HID v1.11 Mouse [Razer Razer DeathAdder Chroma] on usb-0000:05:00.0-2/input0
[    1.646605] input: Razer Razer DeathAdder Chroma as /devices/pci0000:00/0000:00:1c.4/0000:05:00.0/usb3/3-2/3-2:1.1/0003:1532:0043.0004/input/input9
[    1.701903] hid-generic 0003:1532:0043.0004: input,hidraw3: USB HID v1.11 Keyboard [Razer Razer DeathAdder Chroma] on usb-0000:05:00.0-2/input1
[    1.702789] input: Razer Razer DeathAdder Chroma as /devices/pci0000:00/0000:00:1c.4/0000:05:00.0/usb3/3-2/3-2:1.2/0003:1532:0043.0005/input/input10
[    1.757977] hid-generic 0003:1532:0043.0005: input,hidraw4: USB HID v1.11 Keyboard [Razer Razer DeathAdder Chroma] on usb-0000:05:00.0-2/input2
[   16.001820] usb 1-3: device descriptor read/all, error -110
[   16.113756] usb 1-3: new high-speed USB device number 3 using xhci_hcd
[   26.241805] usb 1-3: device descriptor read/all, error -110
[   26.353745] usb 1-3: new high-speed USB device number 4 using xhci_hcd
[   31.369801] usb 1-3: device descriptor read/8, error -110
[   36.489793] usb 1-3: device descriptor read/8, error -110
[   36.705735] usb 1-3: new high-speed USB device number 5 using xhci_hcd
[   41.721789] usb 1-3: device descriptor read/8, error -110
[   46.841785] usb 1-3: device descriptor read/8, error -110
[   46.945737] usb usb1-port3: unable to enumerate USB device
```

the last 30 seconds is what i am guessing is giving me troubles.

this is way out of my league. have only been using linux to learn a bit once in a while. 
Any help would be very appreciated :)

---

### Post by MartyBuntu on 2015-09-08
Is the headset battery powered?

---

### Post by nillerzen on 2015-09-09
No draws power trough the usb, even draws a little bit of power when the pc is shut off.

enough to light the LED's

---

### Post by Bucky Ball on 2015-09-09
Looks to me like lsusb finds it fine, unless you have another razer device plugged in:

```
Bus 003 Device 003: ID 1532:0043 Razer USA, Ltd 
Bus 003 Device 002: ID 1532:010b Razer USA, Ltd 
```

Is that all of the output from dmesg right to the end of the output? If not, restart the machine with the dongle out, once at a stable desktop, plug the device and run:

```
dmesg
```

... immediately. Post the end of the output, all of it, concerning the Razer you just plugged in.

---

### Post by nillerzen on 2015-09-09
No the two razer devices it finds in lsusb is the mouse and keyboard.

i tried what you said and it seems like it gives me the same output

```
[   61.625679] usb 1-3: new high-speed USB device number 6 using xhci_hcd
[   71.753711] usb 1-3: device descriptor read/all, error -110
[   71.865670] usb 1-3: new high-speed USB device number 7 using xhci_hcd
[   81.994353] usb 1-3: device descriptor read/all, error -110
[   82.106287] usb 1-3: new high-speed USB device number 8 using xhci_hcd
[   87.122704] usb 1-3: device descriptor read/8, error -110
[   92.242985] usb 1-3: device descriptor read/8, error -110
[   92.458905] usb 1-3: new high-speed USB device number 9 using xhci_hcd
[   97.475133] usb 1-3: device descriptor read/8, error -110
[  102.595249] usb 1-3: device descriptor read/8, error -110
[  102.699227] usb usb1-port3: unable to enumerate USB device
[  102.811224] usb 1-12: new full-speed USB device number 10 using xhci_hcd
[  102.923983] usb 1-12: Device not responding to setup address.
[  103.127359] usb 1-12: Device not responding to setup address.
[  103.331223] usb 1-12: device not accepting address 10, error -71
[  103.443227] usb 1-12: new full-speed USB device number 11 using xhci_hcd
[  103.571612] usb 1-12: device descriptor read/all, error -71
[  103.683231] usb 1-12: new full-speed USB device number 12 using xhci_hcd
[  103.683322] usb 1-12: Device not responding to setup address.
[  103.887377] usb 1-12: Device not responding to setup address.
[  104.091263] usb 1-12: device not accepting address 12, error -71
[  104.203245] usb 1-12: new full-speed USB device number 13 using xhci_hcd
[  104.203337] usb 1-12: Device not responding to setup address.
[  104.407341] usb 1-12: Device not responding to setup address.
[  104.611256] usb 1-12: device not accepting address 13, error -71
[  104.611274] usb usb1-port12: unable to enumerate USB device
```

---

