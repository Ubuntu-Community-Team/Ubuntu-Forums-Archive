---
title: "USB device requires unplugging and re-plugging to make it work after reboot."
date: 2022-06-01
forum: Hardware
---

### Post by monore on 2022-06-01
I am trying to get a device called [ThingMagic USB Pro UHF Reader]("https://www.jadaktech.com/products/thingmagic-rfid/thingmagic-usb-pro-uhf-reader/") (a USB device) to work properly with a Raspberry Pi 4 and Ubuntu. For the most part, everything works perfectly fine until I reboot or turn the Raspberry Pi off and on, if I do that, the Raspberry Pi no longer recognizes the ThingMagic USB Pro UHF Reader, I must unplug and re-plug the ThingMagic USB cable in order to get things to work again.

Some observations:
[LIST]
[*]If I connect a USB hub to the Raspberry Pi 4 and then I connect the ThingMagic USB Pro UHF Reader device to the USB hub, things sometimes work (the ThingMagic USB Pro UHF Reader device is recognized by the Raspberry Pi 4 automatically after rebooting or turning the Pi on and off). I say sometimes because based on some experimentation, it appears that USB hubs based on USB2 seem to always work work but USB hubs based on USB3 seems to always fail.
[*]When the ThingMagic USB Pro UHF Reader device is connected, if I reboot / restart the OS the mouse and keyboard (connected to other USB ports) will freeze and stay frozen for about a minute or two and then they become available. It seems that all the USB ports stop working while the OS tries to resolve the issues with the ThingMagic USB Pro UHF Reader .
[*]Under the same scenario / conditions, everything works perfectly fine on Windows... say whaaaaat :)
[/LIST]

Below is a snapshot of what I think are the important bits from dmesg (full dmesg below):

```
[COLOR=#24292F][FONT=-apple-system][ 18.014135] usb 1-1.3: device descriptor read/64, error -110[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 31.837036] cam-dummy-reg: disabling[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 33.378065] usb 1-1.3: device descriptor read/64, error -110[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 33.597902] usb 1-1.3: new full-speed USB device number 6 using xhci_hcd[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 48.822642] usb 1-1.3: device descriptor read/64, error -110[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 64.184345] usb 1-1.3: device descriptor read/64, error -110[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 64.304891] usb 1-1-port3: attempt power cycle[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 64.964096] usb 1-1.3: new full-speed USB device number 7 using xhci_hcd[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 65.587170] xhci_hcd 0000:01:00.0: ERROR: unexpected setup address command completion code 0x24.[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 66.427163] xhci_hcd 0000:01:00.0: ERROR: unexpected setup address command completion code 0x24.[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 66.644210] usb 1-1.3: device not accepting address 7, error -22[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 66.744233] usb 1-1.3: new full-speed USB device number 8 using xhci_hcd[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 67.367316] xhci_hcd 0000:01:00.0: ERROR: unexpected setup address command completion code 0x24.[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 68.207179] xhci_hcd 0000:01:00.0: ERROR: unexpected setup address command completion code 0x24.[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 68.424293] usb 1-1.3: device not accepting address 8, error -22[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system][ 68.425031] usb 1-1-port3: unable to enumerate USB device[/FONT][/COLOR]
```

---

### Post by gdesilva on 2022-06-21
Have you seen this? [https://askubuntu.com/questions/644010/ubuntu-cant-read-my-usb-device-descriptor-read-64-error-110](https://askubuntu.com/questions/644010/ubuntu-cant-read-my-usb-device-descriptor-read-64-error-110)

It might offer a solution in your case.

---

