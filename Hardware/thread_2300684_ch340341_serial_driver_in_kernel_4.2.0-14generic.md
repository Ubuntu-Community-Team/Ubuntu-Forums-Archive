---
title: "ch340/341 serial driver in kernel 4.2.0-14generic"
date: 2015-10-27
forum: Hardware
---

### Post by s3cz0ne on 2015-10-27
Hello all,
This is my first post. I am using Kubuntu 15.10 w/ Linux Kernel 4.2.0-14generic. I have a USB->Serial adapter that uses the WinChipHead ch341 as well as a number of arduino nano clones. I have tried to connect with PuTTY, Minicom and moserial. As long as I'm running these as root I get no error but I also don't get a usable connection. If I fiddle with the baud rate I might get some useless characters but nothing more. Ironically I was running a build of Mint with a kernel that was 3.13-3.16(Don't remember) and I had no trouble. The adapter is recognized and is showing up as ttyUSB0. I have posted the relevant portion of the dmesg output below. Any thoughts?

```
[428967.667599] usb 1-1.5: new full-speed USB device number 10 using ehci-pci
[428967.760633] usb 1-1.5: New USB device found, idVendor=1a86, idProduct=7523
[428967.760639] usb 1-1.5: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[428967.760643] usb 1-1.5: Product: USB2.0-Ser!
[428967.761167] ch341 1-1.5:1.0: ch341-uart converter detected
[428967.763671] usb 1-1.5: ch341-uart converter now attached to ttyUSB0


```

TIA

---

