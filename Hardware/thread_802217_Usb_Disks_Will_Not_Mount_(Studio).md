---
title: "Usb Disks Will Not Mount (Studio)"
date: 2008-05-21
forum: Hardware
---

### Post by ubonetu on 2008-05-21
Hi, everybody, thanks for reading:

dmseg output:

```
bones@superBox:~$ dmesg | grep usb
[   13.345268] usbcore: registered new interface driver usbfs
[   13.345297] usbcore: registered new interface driver hub
[   13.345350] usbcore: registered new device driver usb
[   15.686401] usb usb1: configuration #1 chosen from 1 choice
[   15.843311] usb usb2: configuration #1 chosen from 1 choice
[   15.999622] usb usb3: configuration #1 chosen from 1 choice
[   16.063997] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   16.155563] usb usb4: configuration #1 chosen from 1 choice
[   16.264421] usb 1-2: configuration #1 chosen from 1 choice
[   16.311452] usb usb5: configuration #1 chosen from 1 choice
[   16.543125] usb 2-2: new full speed USB device using ohci_hcd and address 2
[   16.549301] usb usb6: configuration #1 chosen from 1 choice
[   16.807601] usb 1-2: USB disconnect, address 2
[   17.272323] usb 6-4: new high speed USB device using ehci_hcd and address 3
[   17.387053] usb 6-4: configuration #1 chosen from 1 choice
[   17.694478] usb 6-6: new high speed USB device using ehci_hcd and address 4
[   17.813633] usb 6-6: configuration #1 chosen from 1 choice
[   18.075507]  sda:<6>usb 1-2: new low speed USB device using ohci_hcd and address 3
[   18.293328] usb 1-2: configuration #1 chosen from 1 choice
[   18.472131] usb 6-4.3: new full speed USB device using ehci_hcd and address 5
[   18.559825] usb 6-4.3: configuration #1 chosen from 1 choice
[   18.737014] usb 6-4.4: new full speed USB device using ehci_hcd and address 6
[   18.824315] usb 6-4.4: configuration #1 chosen from 1 choice
[   19.030448] usb 6-1: new high speed USB device using ehci_hcd and address 7
[   19.154059] usb 6-1: configuration #1 chosen from 1 choice
[   19.155003] usbcore: registered new interface driver hiddev
[   19.159962] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb1/1-2/1-2:1.0/input/input2
[   19.171705] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-2
[   19.171731] usbcore: registered new interface driver usbhid
[   19.171736] /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.942669] usbcore: registered new interface driver libusual
[   31.026453] usbcore: registered new interface driver usb-storage
[   31.026461] usb-storage: device found at 7
[   31.026463] usb-storage: waiting for device to settle before scanning
[   31.228070] usbcore: registered new interface driver uvcvideo
[   31.228986] usblp0: USB Bidirectional printer dev 6 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5411
[   31.229010] usbcore: registered new interface driver usblp
[   31.376150] usbcore: registered new interface driver ndiswrapper
[   36.024124] usb-storage: device scan complete
[   47.464277] usb 6-1: USB disconnect, address 7
[   87.397083] usb 6-1: new high speed USB device using ehci_hcd and address 8
[   99.496946] usb 6-1: device descriptor read/64, error -110
[  144.731231] usb 6-1: new high speed USB device using ehci_hcd and address 9
[  151.237797] usb 6-1: device descriptor read/64, error -110
[  158.942927] usb 6-1: device descriptor read/64, error -110
[  159.028349] usb 6-1: new high speed USB device using ehci_hcd and address 10
[  165.396017] usb 6-1: device descriptor read/64, error -110
[  171.806194] usb 6-1: device descriptor read/64, error -110
[  171.891611] usb 6-1: new high speed USB device using ehci_hcd and address 11
[  178.212402] usb 6-1: device not accepting address 11, error -110
[  178.314364] usb 6-1: new high speed USB device using ehci_hcd and address 12
[  184.094537] usb 6-1: device not accepting address 12, error -110
```

/var/log/messages:

```
bones@superBox:~$ tail /var/log/messages
May 21 07:08:40 superBox kernel: [   48.319251] ACPI: PCI Interrupt 0000:01:05.0[B] -> GSI 19 (level, low) -> IRQ 19
May 21 07:08:41 superBox kernel: [   48.602779] hda-intel: Invalid position buffer, using LPIB read method instead.
May 21 07:08:43 superBox kernel: [   49.730710] [fglrx] GART Table is not in FRAME_BUFFER range 
May 21 07:08:43 superBox kernel: [   49.731497] [fglrx] Reserve Block - 0 offset =  0Xbffb000 length = 0X5000
May 21 07:08:43 superBox kernel: [   49.732387] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
May 21 07:08:43 superBox kernel: [   49.886717] [fglrx] interrupt source 10000000 successfully enabled
May 21 07:08:43 superBox kernel: [   49.887472] [fglrx] enable ID = 0x00000008
May 21 07:08:43 superBox kernel: [   49.887929] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
May 21 07:09:37 superBox kernel: [   87.397083] usb 6-1: new high speed USB device using ehci_hcd and address 8
May 21 07:11:32 superBox kernel: [  144.731231] usb 6-1: new high speed USB device using ehci_hcd and address 9
```

My 1394 drive is fine (though it duplicated itself in /media/).  It mounts and is usable.

I know it's not a bad cable or connection or the bus physically as my other usb devices work (just not my pen-drive or nexBlack player).

Any help greatly appreciated.

ward

---

