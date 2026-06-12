---
title: "A strange problem about USB Mouse Device"
date: 2015-01-26
forum: Hardware
---

### Post by compaq4ml on 2015-01-26
HP COMPAQ laptop
Ubuntu desktop 14.04 LTS
Logitech G1 usb mouse device 


If the OS start up with the usb mouse device pluggin, the mouse device will not work ( the light of USB Mouse is not lighting )
While the OS start up without the usb mouse device, plug it after the OS is starting up , all is ok ( the mouse light is blinking )

There is no special option in BIOS for USB Mouse.



I am puzzled with this strangeproblem :(

---

### Post by compaq4ml on 2015-04-13
I have changed several mouse but the problem is still here.

Sometime move the mouse continuously while ubuntu starting up may active the mouse.
Sometime reboot the OS may be useful.
Sometime no way can solve the strange problem.

Is there some way to active the USB mouse ?

---

### Post by dino99 on 2015-04-13
i suggest you check your bios settings about usb
i myself have a bluetooth logitec mouse wich have a receiver, but never had your issue
do you get some warning/errors logged about either the mouse and/or usb ?

the system , via the kernel, deal with such device, so nothing to do normally. Which kernel is used ?

note: my mouse have 2 buttons under it, and the receiver have one too (kind of reset); maybe yours have some too

---

### Post by Mike_Walsh on 2015-04-13
> **9d9 said:**
> note: my mouse have 2 buttons under it, and the receiver have one too (kind of reset); maybe yours have some too

Doubtful, as this is quite clearly a [COLOR=#ff0000]wired[/COLOR] 'gaming' mouse (and about 10 yrs old at that.)

[https://www.google.co.uk/search?q=logitech+g1+mouse&biw=1024&bih=661&tbm=isch&tbo=u&source=univ&sa=X&ei=OUssVeS0C4LoaO69geAH&ved=0CCgQsAQ](https://www.google.co.uk/search?q=logitech+g1+mouse&biw=1024&bih=661&tbm=isch&tbo=u&source=univ&sa=X&ei=OUssVeS0C4LoaO69geAH&ved=0CCgQsAQ)


Regards,

Mike.

---

### Post by compaq4ml on 2015-04-13
The following information come from /var/log/dmesg:

[    1.699053] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[    1.796264] usb 3-3: New USB device found, idVendor=04f2, idProduct=b40e
[    1.796267] usb 3-3: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    1.796269] usb 3-3: Product: HP Truevision HD
[    1.796270] usb 3-3: Manufacturer: Chicony Electronics Co., Ltd.
[    1.873821] input: ALPS PS/2 Device as /devices/platform/i8042/serio1/input/input6
[    1.888275] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input5
[    1.915316] usb 3-4: new full-speed USB device number 3 using xhci_hcd
[    1.932767] usb 3-4: New USB device found, idVendor=0cf3, idProduct=3121
[    1.932770] usb 3-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.099479] usb 3-5: new full-speed USB device number 4 using xhci_hcd
[    2.118835] usb 3-5: New USB device found, idVendor=24ae, idProduct=1100
[    2.118839] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.118840] usb 3-5: Product: Rapoo 2.4G Wireless Device
[    2.118842] usb 3-5: Manufacturer: RAPOO
[    2.118974] usb 3-5: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.118976] usb 3-5: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.121467] hidraw: raw HID events driver (C) Jiri Kosina
[    2.124502] usbcore: registered new interface driver usbhid
[    2.124505] usbhid: USB HID core driver
[    2.125672] input: RAPOO Rapoo 2.4G Wireless Device as /devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.0/input/input7
[    2.125792] hid-generic 0003:24AE:1100.0001: input,hidraw0: USB HID v1.10 Mouse [RAPOO Rapoo 2.4G Wireless Device] on usb-0000:00:14.0-5/input0
[    2.125898] hid-generic 0003:24AE:1100.0002: hiddev0,hidraw1: USB HID v1.10 Device [RAPOO Rapoo 2.4G Wireless Device] on usb-0000:00:14.0-5/input1

...
...
[   14.676776] usb 3-4: USB disconnect, device number 3
[   14.676781] usbcore: registered new interface driver ath3k
[   14.767211] Linux video capture interface: v2.00
[   14.809170] kvm: disabled by bios
[   14.949577] usb 3-4: new full-speed USB device number 5 using xhci_hcd
[   15.406833] uvcvideo: Found UVC 1.00 device HP Truevision HD (04f2:b40e)
[   15.447122] input: HP Truevision HD as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input10
[   15.447235] usbcore: registered new interface driver uvcvideo
[   15.447235] USB Video Class driver (1.1.1)

OS found the wireless optical mouse device at first.
Why the disconnection occur ?

---

### Post by Vladlenin5000 on 2015-04-13
Now I'm confused...
How is this ```
[    2.125792] hid-generic 0003:24AE:1100.0001: input,hidraw0: USB HID  v1.10 Mouse [RAPOO Rapoo 2.4G Wireless Device] on  usb-0000:00:14.0-5/input0
```a Logitech G1 mouse?

And it's wireless!!

---

### Post by compaq4ml on 2015-04-13
I have changed several mouse devices.
Now a RAPOO mouse device is pluged on the HP laptop.

I want to know why the mouse doesn't work after recognition successfully.

---

### Post by compaq4ml on 2015-04-13
I have tried several mouse device to solve this problem.
When I use G1(wired mouse) the optical light is on at first but off after the OS start up.

Now I use a RAPOO mouse device(wireless mouse).

---

### Post by tgalati4 on 2015-04-14
It's possible that your USB ports are not putting out enough power.  5VDC and 500 mA's may not be enough to run all of your devices.  Try your mouse on another linux machine, preferably a desktop computer.  A 10-year-old mouse will have old capacitors and if they are leaky, then you will get a voltage drop during bootup and thus the device doesn't wake up quickly enough to be connected to the kernel. 

If you unplug it and quickly plug it back in, the leakage is such that you will get higher voltage after plug-in so the mouse wakes up correctly.  Think of it as jump-starting your mouse.  Unless you can open the mouse and test the capacitors, it's time for a new one.

---

