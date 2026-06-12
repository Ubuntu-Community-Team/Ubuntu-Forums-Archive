---
title: "SHANWAN PS3 GamePad - vibration issue when connected wirelessly"
date: 2020-10-14
forum: Hardware
---

### Post by ah-86 on 2020-10-14
I have problems with the vibration of a generic PS3 controller, this happens to me when I connect the controller wirelessly, but when it is connected by the USB cable, it works well.

The problem is that the vibration does not work in the correct way, the vibration works at full speed, and for a long time instead of a second or two.

When I connect the controller by the USB cable, I get these messages from dmesg:

    ```
[21397.801573] usb 3-2: new full-speed USB device number 5 using xhci_hcd
    [21397.951098] usb 3-2: New USB device found, idVendor=054c, idProduct=0268, bcdDevice= 1.00
    [21397.951103] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
    [21397.951106] usb 3-2: Product: PS3 GamePad
    [21397.951108] usb 3-2: Manufacturer: SHANWAN
    [21397.955927] input: SHANWAN PS3 GamePad Motion Sensors as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/0003:054C:0268.0003/input/input29
    [21398.013884] input: SHANWAN PS3 GamePad as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/0003:054C:0268.0003/input/input28
    [21398.014462] sony 0003:054C:0268.0003: input,hiddev0,hidraw1: USB HID v81.10 Joystick [SHANWAN PS3 GamePad] on usb-0000:00:14.0-2/input0
    [21461.499738] usb 3-2: USB disconnect, device number 5
```

but when it is connected by Bluetooth, I get these messages from dmesg:

    [HTML][21471.515216] sony 0005:054C:0268.0004: unknown main item tag 0x0
    [21471.530748] input: Sony PLAYSTATION(R)3 Controller Motion Sensors as /devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12:1.0/bluetooth/hci0/hci0:42/0005:054C:0268.0004/input/input31
    [21471.531075] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12:1.0/bluetooth/hci0/hci0:42/0005:054C:0268.0004/input/input30
    [21471.531283] sony 0005:054C:0268.0004: input,hidraw1: BLUETOOTH HID v80.00 Joystick [Sony PLAYSTATION(R)3 Controller] on 1c:65:9d:82:b0:1c[/HTML]

I think if Bluez recognizes the controller as [SHANWAN PS3 GamePad] instead of [Sony PLAYSTATION(R)3 Controller], the controller will behave correctly, but how can I do that exactly?

I found a similar issue to mine:
[https://forum.batocera.org/d/4471-vibration-generic-ps3-controller](https://forum.batocera.org/d/4471-vibration-generic-ps3-controller)

---

