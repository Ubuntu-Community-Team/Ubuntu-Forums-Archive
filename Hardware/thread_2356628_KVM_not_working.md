---
title: "KVM not working"
date: 2017-03-25
forum: Hardware
---

### Post by a_gautier on 2017-03-25
Hi Forum,
I got a KVM from China, it is working fine under Windows but the keyboard and mouse are not working with Ubuntu (and other Linux versions I tried). I found that they did something pretty bad, they used the USB  Logitech, Inc. Unifying Receiver Vendor and product ID for their switch but, additionally to this bad idea, they were even not capable of fully implement this silly hack.

**lsusb -v** gives with the KVM (significant section only)

```

[FONT=courier new]Bus 001 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver[/FONT]
[FONT=courier new]Device Descriptor:[/FONT]
[FONT=courier new]  bLength                18[/FONT]
[FONT=courier new]  bDescriptorType         1[/FONT]
[FONT=courier new]  bcdUSB               2.00[/FONT]
[FONT=courier new]  bDeviceClass            0 (Defined at Interface level)[/FONT]
[FONT=courier new]  bDeviceSubClass         0 [/FONT]
[FONT=courier new]  bDeviceProtocol         0 [/FONT]
[FONT=courier new]  bMaxPacketSize0         8[/FONT]
[FONT=courier new]  idVendor           0x046d Logitech, Inc.[/FONT]
[FONT=courier new]  idProduct          0xc52b Unifying Receiver[/FONT]
[FONT=courier new]  bcdDevice            1.01[/FONT]
[FONT=courier new]  iManufacturer           0 [/FONT]
[FONT=courier new]  iProduct                0 [/FONT]
[FONT=courier new]  iSerial                 0 [/FONT]
[FONT=courier new]  bNumConfigurations      1[/FONT]
[FONT=courier new]
[/FONT]
```
**lsusb -v** gives with a Logitech mouse

```

[FONT=courier new]Bus 001 Device 012: ID 046d:c247 Logitech, Inc. [/FONT]
[FONT=courier new]Device Descriptor:[/FONT]
[FONT=courier new]  bLength                18[/FONT]
[FONT=courier new]  bDescriptorType         1[/FONT]
[FONT=courier new]  bcdUSB               2.00[/FONT]
[FONT=courier new]  bDeviceClass            0 (Defined at Interface level)[/FONT]
[FONT=courier new]  bDeviceSubClass         0 [/FONT]
[FONT=courier new]  bDeviceProtocol         0 [/FONT]
[FONT=courier new]  bMaxPacketSize0         8[/FONT]
[FONT=courier new]  idVendor           0x046d Logitech, Inc.[/FONT]
[FONT=courier new]  idProduct          0xc247 [/FONT]
[FONT=courier new]  bcdDevice           71.01[/FONT]
[FONT=courier new]  iManufacturer           1 Logitech[/FONT]
[FONT=courier new]  iProduct                2 Gaming Mouse G100[/FONT]
[FONT=courier new]  iSerial                 0 [/FONT]
[FONT=courier new]  bNumConfigurations      1[/FONT]
```


The iManufacturer and iProduct field at 0 on the KVM indicating that there is no description for this fields and as far I understand this is why it is not working. 
When plugin the KVM I got this is dmesg


```
[FONT=courier new][  218.620431] usb 1-1.1: new low-speed USB device number 6 using ehci-pci[/FONT]
[FONT=courier new][  218.716394] usb 1-1.1: New USB device found, idVendor=046d, idProduct=c52b[/FONT]
[FONT=courier new][  218.716400] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0[/FONT]
[FONT=courier new][  218.777390] hidraw: raw HID events driver (C) Jiri Kosina[/FONT]
[FONT=courier new][  218.798459] usbcore: registered new interface driver usbhid[/FONT]
[FONT=courier new][  218.798464] usbhid: USB HID core driver[/FONT]
```


Wen plugin a Logitech mouse


```
[FONT=courier new][ 4070.996932] usb 1-1.2: new full-speed USB device number 12 using ehci-pci[/FONT]
[FONT=courier new][ 4071.092628] usb 1-1.2: New USB device found, idVendor=046d, idProduct=c247[/FONT]
[FONT=courier new][ 4071.092635] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0[/FONT]
[FONT=courier new][ 4071.092639] usb 1-1.2: Product: Gaming Mouse G100[/FONT]
[FONT=courier new][ 4071.092643] usb 1-1.2: Manufacturer: Logitech[/FONT]
[FONT=courier new][ 4071.095239] input: Logitech Gaming Mouse G100 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:046D:C247.000A/input/input16[/FONT]
[FONT=courier new][ 4071.095592] hid-generic 0003:046D:C247.000A: input,hidraw0: USB HID v1.10 Mouse [Logitech Gaming Mouse G100] on usb-0000:00:1a.0-1.2/input0[/FONT]
```

I can see the KVM under [FONT=courier new]/sys/bus/hid/devices/[/FONT] but there is nothing under [FONT=courier new]/sys/bus/hid/drivers/[/FONT] (the Logitech mouse shows [FONT=courier new]/sys/bus/hid/drivers/hid-generic/[/FONT]).

I also captured the USB initialization sequence with Wireshark and after the two first initial packets the exchange is very different when using the KVM (18 packets exchanged) and the Logitech mouse (30 packets exchanged). I can't attach the capture files I get an "invalid files" when trying to load them here.

So obvious question: How to fix this, without recompiling the kernel?
Of course you will say "change the KVM", but I got is for private use and the supplier asks my to pay for the transport fees to send me a new one, so nearly 50% of the cost of the KVM...

I am more a network guy that anything else (Wireshark was a clue ;) ) so my knowledge of Ubuntu and USB is limited. Any help welcome.


Thanks!

---

### Post by wildmanne39 on 2017-03-25
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

