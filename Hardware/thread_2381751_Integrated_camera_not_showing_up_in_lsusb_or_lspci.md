---
title: "Integrated camera not showing up in lsusb or lspci (Thinkpad X230)"
date: 2018-01-05
forum: Hardware
---

### Post by emccorson on 2018-01-05
I'm trying to get the integrated camera on my laptop (Thinkpad X230) to work, but cheese says "No device found". It also doesn't show up in the output of lsusb or lspci. The camera is set to enabled in the BIOS.

lsusb output:
```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lspci output:
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 System peripheral: Ricoh Co Ltd MMC/SD Host Controller (rev 07)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
```

At this point, I'm wondering if it's just a hardware problem. The laptop had Windows installed when I bought it and I stupidly didn't check the camera before I wiped it.

Does anyone know what else I can try?

---

### Post by tokyobadger on 2018-01-05
It might be the hardware configuration issue mentioned in this thread in the lenovo forums
[https://forums.lenovo.com/t5/ThinkPad-X-Series-Laptops/My-new-2306CTO-X230-ThinkPad-is-missing-the-webcam/td-p/826729](https://forums.lenovo.com/t5/ThinkPad-X-Series-Laptops/My-new-2306CTO-X230-ThinkPad-is-missing-the-webcam/td-p/826729)

---

### Post by sccman on 2018-01-05
Can the camera work on another Windows computer? That's an easy way to determine if it's hardware :D

---

### Post by emccorson on 2018-01-05
> **tokyobadger said:**
> It might be the hardware configuration issue mentioned in this thread in the lenovo forums
[https://forums.lenovo.com/t5/ThinkPad-X-Series-Laptops/My-new-2306CTO-X230-ThinkPad-is-missing-the-webcam/td-p/826729](https://forums.lenovo.com/t5/ThinkPad-X-Series-Laptops/My-new-2306CTO-X230-ThinkPad-is-missing-the-webcam/td-p/826729)

I'm pretty sure I have a webcam in the laptop. I didn't buy it directly from Lenovo but I'm sure I can actually see it in the laptop.

> **sccman said:**
> Can the camera work on another Windows computer? That's an easy way to determine if it's hardware :D

It's built-in to the laptop so I don't know how I could check that without pulling the laptop apart.

---

### Post by tokyobadger on 2018-01-06
You could well be right.

From your lspci output
```
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
```
A check at Intel shows that chipset supports MIMO 2x2 
[https://www.intel.com/content/www/us/en/support/articles/000006664/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000006664/network-and-i-o/wireless-networking.html)

It might be interesting to see the output of
```

dmesg | grep -i usb
```
and ```
lsmod | grep uvcvideo
```
Looking at [http://www.thinkwiki.org/wiki/Category:X230](http://www.thinkwiki.org/wiki/Category:X230)
it seems you should be seeing 
```
720p HD [Integrated camera]("http://www.thinkwiki.org/wiki/Integrated_camera") (04f2:b2eb Chicony Electronics Co., Ltd)
```
for the camera and the thinkwiki page states that it should work with the uvcvideo driver so you could try 
```
sudo modprobe uvcvideo
```
If that gets the camera working then you could add uvcvideo to /etc/modules to ensure it always loads

---

### Post by pdc on 2018-01-06
I am sorry I can't offer the definitive fix; but I rather think I have seen several of these posts recently; ...... webcam not showing up and leaving everyone puzzled; I will attempt to provide chapter and verse later

---

### Post by emccorson on 2018-01-07
Unfortunately not getting any output with ```
lsmod | grep uvcvideo
``` and ```
dmesg | grep -i usb
``` doesn't appear to show up anything useful either. I'll post the output just in case I'm missing something:

```
[    0.231650] ACPI: bus type USB registered
[    0.231680] usbcore: registered new interface driver usbfs
[    0.231693] usbcore: registered new interface driver hub
[    0.231718] usbcore: registered new device driver usb
[    1.740431] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.740645] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.758522] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.758587] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.758590] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.758592] usb usb1: Product: EHCI Host Controller
[    1.758594] usb usb1: Manufacturer: Linux 4.10.0-42-generic ehci_hcd
[    1.758595] usb usb1: SerialNumber: 0000:00:1a.0
[    1.758823] hub 1-0:1.0: USB hub found
[    1.759216] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.778520] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.778574] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.778576] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.778578] usb usb2: Product: EHCI Host Controller
[    1.778580] usb usb2: Manufacturer: Linux 4.10.0-42-generic ehci_hcd
[    1.778582] usb usb2: SerialNumber: 0000:00:1d.0
[    1.778805] hub 2-0:1.0: USB hub found
[    1.779059] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.779089] uhci_hcd: USB Universal Host Controller Interface driver
[    1.779263] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.780522] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.780524] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.780526] usb usb3: Product: xHCI Host Controller
[    1.780528] usb usb3: Manufacturer: Linux 4.10.0-42-generic xhci-hcd
[    1.780529] usb usb3: SerialNumber: 0000:00:14.0
[    1.780749] hub 3-0:1.0: USB hub found
[    1.781450] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.781502] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.781504] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.781506] usb usb4: Product: xHCI Host Controller
[    1.781508] usb usb4: Manufacturer: Linux 4.10.0-42-generic xhci-hcd
[    1.781509] usb usb4: SerialNumber: 0000:00:14.0
[    1.781724] hub 4-0:1.0: USB hub found
[    2.086566] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.110506] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.239255] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.239256] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.239746] hub 1-1:1.0: USB hub found
[    2.275102] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.275103] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.275419] hub 2-1:1.0: USB hub found
[    2.526547] usb 1-1.3: new full-speed USB device number 3 using ehci-pci
[    2.660840] usb 1-1.3: New USB device found, idVendor=147e, idProduct=2020
[    2.660841] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.660842] usb 1-1.3: Product: Biometric Coprocessor
[    2.660843] usb 1-1.3: Manufacturer: Auth
[    2.738503] usb 1-1.4: new full-speed USB device number 4 using ehci-pci
[    2.851829] usb 1-1.4: New USB device found, idVendor=0a5c, idProduct=21e6
[    2.851831] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.851832] usb 1-1.4: Product: BCM20702A0
[    2.851833] usb 1-1.4: Manufacturer: Broadcom Corp
[    2.851833] usb 1-1.4: SerialNumber: 2CD05A1D1F0B
[   18.959188] usbcore: registered new interface driver btusb
```

I can do modprobe with uvcvideo but it doesn't affect anything.

---

### Post by tokyobadger on 2018-01-07
In this post [https://askubuntu.com/questions/461657/integrated-webcam-not-detected-after-update-to-14-04](https://askubuntu.com/questions/461657/integrated-webcam-not-detected-after-update-to-14-04) it seems that pressing FN + the Camera key (maybe F10 for you) will activate the camera

---

### Post by sccman on 2018-01-09
It could be that the camera isn't on.

We know that Ubuntu can't detect the camera at all if it isn't in lspci.

If the camera is on and it still doesn't work, try this page:

[https://wiki.archlinux.org/index.php/webcam_setup](https://wiki.archlinux.org/index.php/webcam_setup)

---

### Post by meijer.o on 2018-01-10
Dear linux user,

Have you checked the bios settings? It might be disabled there.

And this I found on the Lenovo forums:

X230 - camera stopped working 
It can be turned on by pressing  Fn+F6.

---

### Post by emccorson on 2018-01-31
I checked the BIOS and the camera is definitely enabled, and I tried the keys that looked like they could be camera keys but still no luck.

I guess it must have been a hardware problem. The laptop also had some other problems so in the end I returned it to the shop. I'll mark this thread as solved in case anyone else is having similar problems.

---

