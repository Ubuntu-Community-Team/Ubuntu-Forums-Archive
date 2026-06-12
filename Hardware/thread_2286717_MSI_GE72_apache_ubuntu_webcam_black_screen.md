---
title: "MSI GE72 apache ubuntu webcam black screen"
date: 2015-07-14
forum: Hardware
---

### Post by Silpion on 2015-07-14
Hi, I use Ubuntu 14.04 LTS edition along with my new, brand MSI GE72 2QD laptop. It's my second choice after Toshiba Qosmio which I've had to return because of totally broken battery.
Anyway, everything works like charm giving me lot of happiness but today, I've noticed that webcam doesn't work at all.

Yes, I've tried using fn+F6 combination. Running the cheese app turns on the webcam light but the screen is totally black.

Ubuntu Multimedia System Selector outputs me 2 devices for Video for Linux 2 (v4l2), default and usb 2 (!?) but none of them works.

Complete lsusb output is:
```

silpion@LCB:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 064e:e390 Suyin Corp. 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 003: ID 1770:ff00  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I've tried even using uvcvideo package but the make result is make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.

Any clue how to fix it? I've already ran off any ideas and internet sources for the topic.
I don't want to lose 1 month without a laptop for sending it back to the service :/

---

### Post by Silpion on 2015-07-14
One more, dmesg output

> [    2.230949] usb 1-1.4: Product: USB 2.0 Webcam Device
[    2.230951] usb 1-1.4: Manufacturer: SuYin
[    2.230952] usb 1-1.4: SerialNumber: HF1017-T840-SE02-REV0801
[    2.238513] media: Linux media interface: v0.10
[    2.241982] Linux video capture interface: v2.00
[    2.248863] uvcvideo: Found UVC 1.00 device USB 2.0 Webcam Device (064e:e390)
[    2.250517] input: USB 2.0 Webcam Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input16



---

### Post by Silpion on 2015-12-31
I've found it out nearly almost half a year after. My build in webcam was fixed after installing nvidia drives.
Ran in the terminal: 

> sudo apt-get install nvidia-current

---

