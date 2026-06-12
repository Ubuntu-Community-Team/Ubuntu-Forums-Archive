---
title: "USB Sound, specifically Topping VX2 DAC / TriPath amp"
date: 2016-11-08
forum: Hardware
---

### Post by Keith_Beef on 2016-11-08
I recently got a little TriPath amp with a built-in DAC, and I'm trying to get it to work with my main desktop computer running 14.04.

Here's what I see:

```
$ lsusb -t
/:  Bus 11.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 10.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class=Audio, Driver=snd-usb-audio, 12M
    |__ Port 2: Dev 2, If 1, Class=Audio, Driver=snd-usb-audio, 12M
    |__ Port 2: Dev 2, If 2, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class=Hub, Driver=hub/3p, 12M
        |__ Port 1: Dev 3, If 0, Class=Wireless, Driver=btusb, 12M
        |__ Port 1: Dev 3, If 1, Class=Wireless, Driver=btusb, 12M
        |__ Port 1: Dev 3, If 2, Class=Vendor Specific Class, Driver=, 12M
        |__ Port 1: Dev 3, If 3, Class=Application Specific Interface, Driver=, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    |__ Port 4: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 5, If 0, Class=Hub, Driver=hub/4p, 480M
            |__ Port 3: Dev 6, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
            |__ Port 3: Dev 6, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
            |__ Port 4: Dev 7, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M

$ dmesg | grep -i topping
[    2.279651] usb 5-2: Manufacturer: TOPPING
[    2.812694] input: TOPPING VX2 as /devices/pci0000:00/0000:00:1a.1/usb5/5-2/5-2:1.2/input/input3
[    2.812774] hid-generic 0003:040D:3400.0001: input,hidraw0: USB HID v1.00 Device [TOPPING VX2] on usb-0000:00:1a.1-2/input2


$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9200000 irq 46
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf6000000 irq 17
 2 [VX2            ]: USB-Audio - VX2
                      TOPPING VX2 at usb-0000:00:1a.1-2, full speed

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: VX2 [VX2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
  
Gnome ALSA mixer sees it as a third device named USB mixer, there is a checked box for PCM
but no controls are visible.

What can I do next?

---

### Post by Keith_Beef on 2016-11-11
Well, I connected this amp to the computer's S/PDIF optical output, just to make sure that the amplifier side of the thing was working. All's fine there. I'd still like to get the USB DAC working, though.

---

