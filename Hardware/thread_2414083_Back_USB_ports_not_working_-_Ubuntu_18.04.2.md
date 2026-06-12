---
title: "Back USB ports not working - Ubuntu 18.04.2"
date: 2019-03-05
forum: Hardware
---

### Post by Natetronn on 2019-03-05
I keep loosing my back USB ports. The front USB ports are fine but, the back ones stop working. I've tried a few things with various degrees of success but, ultimately after reboots the back ports stop working; though I've had them working on several occasions.

I tried resetting to default in the BIOS. I have a [MSI z97s SLI Krait Edition MOBO.]("https://us.msi.com/Motherboard/Z97S-SLI-Krait-Edition.html")

I also tried adding the following in /etc/default/grub per [this suggestion]("https://unix.stackexchange.com/a/175035/34644").

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"
```

And I tried [this]("http://https://askubuntu.com/a/887686/403296"):
```
GRUB_CMDLINE_LINUX="iommu=soft"
```

Note: For this question, I've removed those GRUB lines to start fresh, as I wasn't 100% sure they were effective or not. As seen by the following command autosuspend is back to 2.

```
&#10140;  ~ cat /sys/module/usbcore/parameters/autosuspend
2
```
 
```
&#10140;  ~ lsusb   
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 011: ID 05ac:024f Apple, Inc. 
Bus 003 Device 012: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 010: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 003 Device 004: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver
Bus 003 Device 003: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 003 Device 002: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
&#10140;  ~ uname -r
4.18.0-15-generic
```

```
&#10140;  ~ cat /sys/bus/usb/devices/usb*/power/control                 
auto
auto
auto
auto
```

```
&#10140;  ~ dmesg | grep "usb"
[    0.090242] usbcore: registered new interface driver usbfs
[    0.090242] usbcore: registered new interface driver hub
[    0.090242] usbcore: registered new device driver usb
[    0.544073] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 4.18
[    0.544074] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.544075] usb usb1: Product: EHCI Host Controller
[    0.544076] usb usb1: Manufacturer: Linux 4.18.0-15-generic ehci_hcd
[    0.544077] usb usb1: SerialNumber: 0000:00:1a.0
[    0.564060] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 4.18
[    0.564061] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.564062] usb usb2: Product: EHCI Host Controller
[    0.564063] usb usb2: Manufacturer: Linux 4.18.0-15-generic ehci_hcd
[    0.564063] usb usb2: SerialNumber: 0000:00:1d.0
[    0.565562] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 4.18
[    0.565563] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.565564] usb usb3: Product: xHCI Host Controller
[    0.565565] usb usb3: Manufacturer: Linux 4.18.0-15-generic xhci-hcd
[    0.565566] usb usb3: SerialNumber: 0000:00:14.0
[    0.569446] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 4.18
[    0.569447] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.569448] usb usb4: Product: xHCI Host Controller
[    0.569449] usb usb4: Manufacturer: Linux 4.18.0-15-generic xhci-hcd
[    0.569449] usb usb4: SerialNumber: 0000:00:14.0
[    0.880008] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.900026] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    0.904011] usb 3-2: new high-speed USB device number 2 using xhci_hcd
[    1.036368] usb 1-1: New USB device found, idVendor=8087, idProduct=8009, bcdDevice= 0.00
[    1.036369] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.052649] usb 3-2: New USB device found, idVendor=0bda, idProduct=b812, bcdDevice= 2.10
[    1.052650] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.052651] usb 3-2: Product: 802.11ac NIC
[    1.052652] usb 3-2: Manufacturer: Realtek
[    1.052652] usb 3-2: SerialNumber: 123456
[    1.060381] usb 2-1: New USB device found, idVendor=8087, idProduct=8001, bcdDevice= 0.00
[    1.060382] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.176038] usb 3-5: new high-speed USB device number 3 using xhci_hcd
[    1.325144] usb 3-5: New USB device found, idVendor=090c, idProduct=1000, bcdDevice=11.00
[    1.325145] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.325146] usb 3-5: Product: Flash Drive
[    1.325147] usb 3-5: Manufacturer: Samsung
[    1.325147] usb 3-5: SerialNumber: 27837823478234789234
[    1.452010] usb 3-6: new low-speed USB device number 4 using xhci_hcd
[    1.606024] usb 3-6: New USB device found, idVendor=046d, idProduct=c521, bcdDevice=57.01
[    1.606025] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.606036] usb 3-6: Product: USB Receiver
[    1.606036] usb 3-6: Manufacturer: Logitech
[    1.736035] usb 3-8: new high-speed USB device number 5 using xhci_hcd
[    1.892470] usb 3-8: New USB device found, idVendor=05ac, idProduct=1006, bcdDevice=96.15
[    1.892471] usb 3-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.892482] usb 3-8: Product: Keyboard Hub
[    1.892482] usb 3-8: Manufacturer: Apple, Inc.
[    1.892483] usb 3-8: SerialNumber: 000000000000
[    1.896492] usb-storage 3-5:1.0: USB Mass Storage device detected
[    1.897882] scsi host6: usb-storage 3-5:1.0
[    1.897943] usbcore: registered new interface driver usb-storage
[    1.898797] usbcore: registered new interface driver uas
[    1.904483] usbcore: registered new interface driver usbhid
[    1.904483] usbhid: USB HID core driver
[    1.905864] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/0003:046D:C521.0001/input/input3
[    1.905933] hid-generic 0003:046D:C521.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-6/input0
[    1.906045] input: Logitech USB Receiver Consumer Control as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.1/0003:046D:C521.0002/input/input4
[    1.964317] hid-generic 0003:046D:C521.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-6/input1
[    2.184015] usb 3-8.2: new low-speed USB device number 6 using xhci_hcd
[    2.294465] usb 3-8.2: New USB device found, idVendor=05ac, idProduct=024f, bcdDevice= 0.74
[    2.294467] usb 3-8.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.294468] usb 3-8.2: Product: Apple Keyboard
[    2.294469] usb 3-8.2: Manufacturer: Apple Inc.
[    2.555659] usb 3-8.1: new full-speed USB device number 7 using xhci_hcd
[    2.767383] usb 3-8.1: New USB device found, idVendor=0a12, idProduct=0001, bcdDevice= 1.00
[    2.767385] usb 3-8.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.767386] usb 3-8.1: Product: Bluetooth V2.0 Dongle
[    2.767387] usb 3-8.1: Manufacturer: Bluetooth v2.0
[    2.803766] usbcore: registered new interface driver rtl88x2bu
[    2.888766] input: Apple Inc. Apple Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8.2/3-8.2:1.0/0003:05AC:024F.0003/input/input15
[    2.890824] usbcore: registered new interface driver btusb
[    2.948906] apple 0003:05AC:024F.0003: input,hidraw2: USB HID v1.11 Keyboard [Apple Inc. Apple Keyboard] on usb-0000:00:14.0-8.2/input0
[    2.949010] input: Apple Inc. Apple Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8.2/3-8.2:1.1/0003:05AC:024F.0004/input/input16
[    3.008239] apple 0003:05AC:024F.0004: input,hidraw3: USB HID v1.11 Device [Apple Inc. Apple Keyboard] on usb-0000:00:14.0-8.2/input1
[   15.842968] input: My Trackpad as /devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8.1/3-8.1:1.0/bluetooth/hci0/hci0:11/0005:05AC:030E.0005/input/input21
[ 1153.410712] usb 3-5: USB disconnect, device number 3



```

Any help on how to proceed with addressing this issue would be greatly appreciated.

---

### Post by him610 on 2019-03-05
Okay Natetronn,

Do you have anything connected to your MB USB expansion connectors
JUSB1~2 USB 2.0 Expansion Connectors
JUSB3 USB 3.0 Expansion Connector 

Do you have good, undamaged USB cables connected to your USB devices?
Does you USB connection issue include both USB 2.0 and USB 3.0 ports?

This is from page 3-12 of you MB user manual, E7922v2.pdf,
> 
&#9654; &#9654; Legacy USB Support [Enabled]
Sets Legacy USB function support.
[Auto] The system will automatically detect if any USB device is connected
and enables or disables the legacy USB support.
[Enabled] Enable the USB support for legacy operating systems that do not
support USB.
[Disabled] The USB devices are available only for UEFI applications.

How is yours set?

One way to possibly narrow it down is through process of elimination.
Connect your keyboard and mouse to the USB 2 ports underneath the PS/2 Keyboard/mouse Combo Port.
1. Disconnect all external USB devices that are not necessary for the operation of your system. 
2. Let the system operate longer than the expected time you would normally lose connectivity to the USB ports.
3. One by one, reconnect each remaining external USB device, waiting between each the time you waited in step 2.

Keep a record of each step and its results. If and when the connection fails, you will have a good idea what caused the failure.

Let us know how it goes.

---

### Post by Natetronn on 2019-03-05
Hey him610, thanks for the reply!

Okay, I may have narrowed it down. I'll need more time to verify, of course but, for now...

The Apple Keyboard w/ numpad may be the issue. It would work on port 2 some of the time but, not at other times. I have another apple keyboard, smaller non-numpad, that fires right up in port 1 and 2. And after plugging in that one I'd try that initial numpad keyboard again and it would work but, then I'd try a different port with it and it wouldn't work etc. I can see all of this from the bios's mobo explorer diagram, which shows actual usb devices being plugged in and out in real time.

Note: the keyboard works fine on a Mac and seemed to work okay on the rear 3.0 ports.

I'll update over the next couple days if everything is fine and switch the thread to solved.

For now, however, I'm going to answer the questions and this just in case I haven't solved the issue with what appears to be a touchy Apple USB keyboard. Plus, it may be helpful for others who may come across this thread.

> JUSB1~2 USB 2.0 Expansion Connectors
JUSB3 USB 3.0 Expansion Connector

I have one 3.0 port on the top of the case. 3.0 cable is plugged into JUSB3.
I have three 2.0 ports on the top of the case. Two 2.0 cables plugged in to JUSB1 and JUSB2. (looks like this could handle 4 ports, 2 each but, there are only 3 on the case.)

I can see all front ports functioning on the mobo explorer and they seemed to work well the whole time anyway. And this even with the touchy keyboard.

> Do you have good, undamaged USB cables connected to your USB devices?

I wasn't using any USB cables, only dongles and the keyboard, which includes a USB cable. I was using the keyboard hub as well for the Bluetooth dongle.

> Does you USB connection issue include both USB 2.0 and USB 3.0 ports?

The 3.0 all seemed to be fine for the touchy keyboard. It was only the 2.0 1&2 ports that weren't playing nice and this according to mobo explorer (and initial issue) 

(I kept using the 2.0 ports for the keyboard and hadn't tried any 3.0 as I was saving those for 3.0 devices instead.)

In regards to Legacy USB Support, it was set to Enabled, which I believe is the default for Optimized Settings (once I'm satisfied things are working again I may set that to auto?)

Anyway, I'll update this if things change. Thanks again!

---

