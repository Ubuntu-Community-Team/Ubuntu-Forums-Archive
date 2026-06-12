---
title: "USB 3.0 device only works in 3.1 Gen 2 port?"
date: 2020-12-02
forum: Hardware
---

### Post by &amp;KyT$0P# on 2020-12-02
I have a System76 Thelio Major with Intel CPU, with USB ports as shown [here]("https://tech-docs.system76.com/models/thelio-major-intel-and-amd/external-overview.html").  All of my USB ports work.  But one of my USB devices only works in the 3.1 Gen 2 (red) port?

If I plug it in any of the USB 3.0 (blue) ports, it doesn't work.  I just get messages like this in syslog -
```
kernel: [ 2148.773358] usb usb2-port6: Cannot enable. Maybe the USB cable is bad?
```

I also tried plugging it into the USB-C port, using a dongle (which I verified working).  In one orientation of the dongle, I get same result as plugging into the USB 3.0 port.  So I tried flipping it over, but that doesn't work either and syslog gets spammed, here's a sample -
```
kernel: [ 8325.157013] usb 4-2: Device not responding to setup address.
kernel: [ 8325.365022] usb 4-2: Device not responding to setup address.
kernel: [ 8325.572806] usb 4-2: device not accepting address 2, error -71
kernel: [ 8325.769433] usb 4-2: new SuperSpeed Gen 1 USB device number 3 using xhci_hcd
kernel: [ 8325.794544] usb 4-2: New USB device found, idVendor=1f75, idProduct=0611, bcdDevice= 0.06
kernel: [ 8325.794548] usb 4-2: New USB device strings: Mfr=4, Product=5, SerialNumber=6
kernel: [ 8325.794550] usb 4-2: SerialNumber: <xxxxxxxx>
mtp-probe: checking bus 4, device 3: "/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/usb4/4-2"
mtp-probe: bus: 4, device: 3 was not an MTP device
kernel: [ 8325.898987] usb-storage 4-2:1.0: USB Mass Storage device detected
kernel: [ 8325.899126] scsi host8: usb-storage 4-2:1.0
kernel: [ 8325.899199] usbcore: registered new interface driver usb-storage
kernel: [ 8325.933688] usbcore: registered new interface driver uas
mtp-probe: checking bus 4, device 3: "/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/usb4/4-2"
mtp-probe: bus: 4, device: 3 was not an MTP device
kernel: [ 8326.440813] usb 4-2: USB disconnect, device number 3
kernel: [ 8327.073447] usb 4-2: new SuperSpeed Gen 1 USB device number 4 using xhci_hcd
kernel: [ 8327.098750] usb 4-2: New USB device found, idVendor=1f75, idProduct=0611, bcdDevice= 0.06
kernel: [ 8327.098754] usb 4-2: New USB device strings: Mfr=4, Product=5, SerialNumber=6
kernel: [ 8327.098757] usb 4-2: SerialNumber: <xxxxxxxx>
kernel: [ 8327.107970] usb 4-2: can't set config #1, error -32
mtp-probe: checking bus 4, device 4: "/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/usb4/4-2"
mtp-probe: bus: 4, device: 4 was not an MTP device
mtp-probe: checking bus 4, device 4: "/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/usb4/4-2"
mtp-probe: bus: 4, device: 4 was not an MTP device
kernel: [ 8327.388791] usb 4-2: USB disconnect, device number 4
kernel: [ 8327.729342] usb 4-2: new SuperSpeed Gen 1 USB device number 5 using xhci_hcd
kernel: [ 8327.754741] usb 4-2: New USB device found, idVendor=1f75, idProduct=0611, bcdDevice= 0.06
kernel: [ 8327.754744] usb 4-2: New USB device strings: Mfr=4, Product=5, SerialNumber=6
kernel: [ 8327.754747] usb 4-2: SerialNumber: <xxxxxxxx>
kernel: [ 8327.762337] usb-storage 4-2:1.0: USB Mass Storage device detected
kernel: [ 8327.762741] scsi host8: usb-storage 4-2:1.0
mtp-probe: checking bus 4, device 5: "/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/usb4/4-2"
mtp-probe: bus: 4, device: 5 was not an MTP device
mtp-probe: checking bus 4, device 5: "/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/usb4/4-2"
mtp-probe: bus: 4, device: 5 was not an MTP device
kernel: [ 8328.488798] usb 4-2: USB disconnect, device number 5
kernel: [ 8331.753343] usb 4-2: new SuperSpeed Gen 1 USB device number 6 using xhci_hcd
kernel: [ 8331.880806] usb 4-2: new SuperSpeed Gen 1 USB device number 6 using xhci_hcd
kernel: [ 8332.205002] usb 4-2: Device not responding to setup address.
kernel: [ 8332.413015] usb 4-2: Device not responding to setup address.
kernel: [ 8332.620804] usb 4-2: device not accepting address 7, error -71
kernel: [ 8332.620869] usb usb4-port2: attempt power cycle

```

I had no issue using this same USB device in my old MacBook Pro 9,1.

The USB device in question is a Inateck SATA/IDE to USB 3.0 adapter.  I can reproduce this problem with or without any disk actually attached to it.  I always plug in the device's own power supply when I use it.

Why does this USB 3.0 device require the USB 3.1 Gen 2 port?  Why doesn't it work in this computer's USB 3.0 ports?

---

### Post by &amp;KyT$0P# on 2020-12-06
bump

---

### Post by rbmorse on 2020-12-06
I've got a Rosewill (or maybe Orico...I forget) adapter that's like that. 

You want to know the real killer?  The device works flawlessly on every port when the machine is running Windows.

---

### Post by &amp;KyT$0P# on 2020-12-12
Thanks for the feedback rbmorse.  So you're saying this is likely a software issue?  Do you know whether this is yet resolved in *buntu 20.10 or later?

---

### Post by &amp;KyT$0P# on 2021-01-03
bump

---

### Post by &amp;KyT$0P# on 2021-01-06
bump

---

### Post by &amp;KyT$0P# on 2021-01-11
bump

---

### Post by Autodave on 2021-01-11
It is hard to say for sure.  I have a particular drive here that will not run on one particular USB 3.0 port.  The real kicker is that it *will* work on the one right next to it which is wired together.  Why?  Dunno.  It is just that way.  I have several other 3.0 sticks that work just fine in either, but that one particular one does not.

---

### Post by &amp;KyT$0P# on 2021-01-12
Thanks for the replies.  I think expanding my search to include these details maybe getting somewhere.

As shown in [screenshots of EFI settings]("https://tech-docs.system76.com/models/thelio-major-intel-and-amd/repairs.html#bios") suggest the motherboard of this computer might be a Gigabyte.  And searching shows that apparently a lot of people have USB issues like this when running Linux on a Gigabyte motherboard.  The fix involves something about IOMMU and various related EFI settings and Linux boot parameters.  But the problems described are not identical to this one, and I don't know enough to parse beyond what I write in this post or determine what might be relevant for me?  And it sounds like doing the wrong thing could leave me with no USB devices working at all :o

Does any of this IOMMU stuff have any applicability to my situation?
If so, what changes exactly do I need to make?

---

### Post by &amp;KyT$0P# on 2021-01-16
> **halogen2 said:**
> If I plug it in any of the USB 3.0 (blue) ports, it doesn't work.  I just get messages like this in syslog -
```
kernel: [ 2148.773358] usb usb2-port6: Cannot enable. Maybe the USB cable is bad?
```

I went through my EFI settings, and found a setting "xHCI Handoff" that was set to Disabled.  Enabling that did not get this working, but the syslog messages like quoted above are now interspersed with messages like this every so often -
```
kernel: [  282.270345] usb 1-6: new high-speed USB device number 10 using xhci_hcd
```
Does this difference mean anything relevant?

I did not find any setting about "IOMMU" in my EFI (although searching suggests it maybe called something else?).  Should I do something with [FONT=Courier New]iommu=[/FONT] boot parameter?  How safe is it to just try various values?

---

### Post by #&amp;thj^% on 2021-01-16
hey h2, I've found on most of my Devices/Computers:
*** My theory is that usb "legacy" conflicts with the os's understanding of 3.0,

You can check your USB devices with:
 ```
lsusb -t
```
 There should also be listed which driver is in use and at which speed the devices are connected. 
EX:
```

/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 10000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 10000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
    |__ Port 3: Dev 2, If 0, Class=Mass Storage, Driver=uas, 480M
    |__ Port 8: Dev 3, If 1, Class=Video, Driver=uvcvideo, 480M
    |__ Port 8: Dev 3, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 9: Dev 4, If 0, Class=Vendor Specific Class, Driver=, 12M
    |__ Port 10: Dev 5, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 10: Dev 5, If 1, Class=Wireless, Driver=btusb, 12M


```
>>> back into bios, have usb 3.0 turned on, and any other options turned on, but turn off legacy usb option. (If available)

[U]Also you could also try adding, "iommu=soft" to the boot parameters.
[/U]
My understanding, **"iommu=soft"** means use some "software" version of iommu instead of "hardware" support from the motherboard. Also, the **iommu=pt parameter should prevent **Linux from touching devices which cannot be passed through.

What I have noticed though throughout the years transfer speeds vary from 120mb's to 50-60mb's

---

### Post by &amp;KyT$0P# on 2021-01-16
> **1fallen said:**
> >>> back into bios, have usb 3.0 turned on, and any other options turned on, but turn off legacy usb option. (If available)

Tried Legacy USB mode set to Auto and Disabled, both with xHCI Hand-off Enabled.  Unfortunately it didn't make any difference :(

> [U]Also you could also try adding, "iommu=soft" to the boot parameters.
[/U]

This did not make any difference either, nor did [FONT=Courier New]iommu=pt[/FONT].  But I didn't leave the EFI settings changes in place while trying this, I had reset the EFI settings after seeing those changes not help.  To be clear, should I have done all this at once?

---

### Post by #&amp;thj^% on 2021-01-16
> **halogen2 said:**
>   To be clear, should I have done all this at once?

As of this point now, when booting...select kernel...press "e" then add <iommu=soft> to the kernel line:
```
GRUB_CMDLINE_LINUX_DEFAULT=
```
I'm not sure how you added it, but if_ you _edited "/etc/default/grub" and then updated-grub for the system to use that new parameter. Without messing in UEFI or Bios this run.

---

### Post by &amp;KyT$0P# on 2021-01-16
> **1fallen said:**
> _ you _edited "/etc/default/grub" and then updated-grub for the system to use that new parameter. 

Yes, that's how I added the boot parameter.

> **halogen2 said:**
> To be clear, should I have done all this at once?

I went ahead and tested anyway doing all the combinations of both the EFI changes and [FONT=Courier New]iommu=[/FONT] boot parameter changes 1fallen mentioned.  Sadly, none of it helped :(

I'm thinking maybe at this point I would best shelve this until I can update the kernel or entire OS to a more recent version (or if I receive a EFI update?).  But I'd appreciate any other suggestions :)

---

### Post by #&amp;thj^% on 2021-01-16
Well at least we figured out a couple more ways that don't work. ;)

---

### Post by &amp;KyT$0P# on 2021-06-16
For unrelated reasons, I now have also a laptop, also System76 brand.  There this issue only occurs in one USB 3 port, while a second USB 3 port and the USB 2.0 port have no problem handling this device.  That's good enough for me that I didn't bother testing the USB-C port.

Since I have now at least three USB ports that work with the device, I no longer feel uncomfortable just living with this.  Still, I'd rather have this working if possible.

* I have now tested this in Pop!_OS 21.04 on the Thelio Major.  No difference to this issue.

---

### Post by &amp;KyT$0P# on 2021-07-04
Found a workaround.  I plugged in a USB **2.0** hub into one of the problematic USB 3.0 ports, and then plugged in my adapter into that USB 2.0 hub.  And it works! :D

So, solved for purpose of this forum thread.  But I probably should try to reach out to System76 about this, I would think something is wrong if I have to hardware-force USB 2.0 on a USB 3.0 device.

---

