---
title: "Getting a Zebex Z-6010 series USB barcode scanner working on Xubuntu"
date: 2008-11-20
forum: Hardware
---

### Post by sternocera on 2008-11-20
Hello all,

I'm attempting to get a Taiwanese USB barcode scanner, the Zebex Z-6010 series, working with Xubuntu 8.04. The device "just works" as a HID on another Linux system, running Opensuse 11, so I expected the same from Xubuntu. However, it does not "just work" :-( on Xubuntu.

When I plug in the scanner on Xubuntu, and scan a barcode, the barcode scans, but not correctly: The light of the Zebex goes from blue to red, and makes a beep, but stays on red and remains unresponsive. I would expect it to go from blue to red, beep, and then go quickly back to blue. It's as if it's getting stuck on red. However, a device does appear under /dev/input/event7.

If I "modprobe usbkbd", nothing changes. I still observe exactly the same behaviour.

Here is the dmesg output of that system when the device is plugged into the Opensuse 11 system, where it works:
```

bootsplash: status on console 0 changed to on
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:19:21:f8:49:62:00:1e:2a:dc:cd:d5:08:00 SRC=10.0.0.2 DST=10.0.0.60 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2048 DPT=137 LEN=58
usb 5-1: new low speed USB device using uhci_hcd and address 2
usb 5-1: new device found, idVendor=0000, idProduct=0001
usb 5-1: new device strings: Mfr=0, Product=0, SerialNumber=0
usb 5-1: configuration #1 chosen from 1 choice
input: HID 0000:0001 as /class/input/input6
input: USB HID v1.00 Keyboard [HID 0000:0001] on usb-0000:00:10.3-1
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=10.0.0.60 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44

```

Here is the dmesg output from the Xubuntu 8.04 system, where it does not work:
```

375a376,381
[  861.082779] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  861.237962] usb 2-1: configuration #1 chosen from 1 choice
[  861.255358] input: HID 0000:0001 as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input7
[  861.282863] input,hidraw1: USB HID v1.00 Keyboard [HID 0000:0001] on usb-0000:00:1d.1-1
[  861.697986] usbcore: registered new interface driver usbkbd
[  861.698518] /build/buildd/linux-2.6.24/drivers/hid/usbhid/usbkbd.c: :USB HID Boot Protocol keyboard driver

```

*Please* offer any help or advice that you can in getting this damn thing to work as desired. It's very important to me that I get it to work. 

Thanks,
Sternocera

---

### Post by sternocera on 2008-11-20
I booted the Xubuntu 8.04 live CD on the Opensuse 11 machine - I can confirm that I experience exactly the same issue and symptoms there as I do on the other Xubuntu 8.04 machine. This is helpful, as it isolates the problem to Xubuntu 8.04 .

Thanks,
Sternocera

---

### Post by andrevanzuydam on 2009-01-21
These scanners normally come with a setup mode - make sure the interface mode is USB.  Then try the following which worked for me.

sudo modprobe usbkbd

I'm not sure whether one would have to put that in a script on boot but at least the scanner works.

---

### Post by Busterdog on 2009-11-10
This was working on Jaunty. It stopped working on Karmic. 
Now I get 
FATAL: Module usbkbd not found.
I tried the blacklist fix mentioned elsewhere, but it kills my keyboard, mouse and the barcode scanner still doesn't work.

---

### Post by summetj on 2010-05-31
> **Busterdog said:**
> This was working on Jaunty. It stopped working on Karmic. 
Now I get 
FATAL: Module usbkbd not found.
I tried the blacklist fix mentioned elsewhere, but it kills my keyboard, mouse and the barcode scanner still doesn't work.

Same problem here with 9.10 and a Acan FG-8100 barcode reader. I've tested with Ubuntu 10.04 and the upstream kernal patch hasn't made it in, so upgrading won't help.

I don't want to have to re-compile the whole kernel, anybody know an easy way to install/compile just the usbkbd module?

Jay

---

