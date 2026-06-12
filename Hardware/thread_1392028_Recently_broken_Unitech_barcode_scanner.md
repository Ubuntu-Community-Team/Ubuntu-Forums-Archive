---
title: "Recently broken Unitech barcode scanner"
date: 2010-01-27
forum: Hardware
---

### Post by pontifier on 2010-01-27
I have a unitech ms-180 barcode scanner.

It worked in ubuntu 8.04, but in 9.04 and 9.10 it crashes the user session back to the login screen when it scans a barcode.
This error is extremely repeatable (every scan causes a crash), and was tried on 2 different computers with the exact same effect.

It seems to work correctly when connected through ubuntu to a qemu virtual machine running xp, and does not crash the ubuntu session in this case.

the vendor/product ID is: 04b4:de64

dmesg on connect:
```
[11653.788087] usb 2-1: new low speed USB device using ohci_hcd and address 3
[11653.997566] usb 2-1: configuration #1 chosen from 1 choice
[11654.548415] input: Guest Generic DE64-401 as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input10
[11654.548659] cypress 0003:04B4:DE64.0002: input,hidraw1: USB HID v1.00 Keyboard [Guest Generic DE64-401] on usb-0000:00:13.0-1/input0

```

I have no idea what the problem is. The scanner is supposed to emulate a keyboard, and that seems to be what is going on.

---

### Post by axelb on 2010-06-25
Perhaps the same problem as in these posting:

[http://ubuntuforums.org/showthread.php?t=1112575](http://ubuntuforums.org/showthread.php?t=1112575) (this gives the most information of those that I have found)
[http://ubuntuforums.org/showpost.php?p=776752&postcount=2](http://ubuntuforums.org/showpost.php?p=776752&postcount=2)
[http://ubuntuforums.org/showthread.php?t=1329724](http://ubuntuforums.org/showthread.php?t=1329724)
[http://www.linuxforums.org/forum/ubuntu-help/156109-barcode-reader-will-not-work-properly-9-10-a.html](http://www.linuxforums.org/forum/ubuntu-help/156109-barcode-reader-will-not-work-properly-9-10-a.html)
[http://ubuntuforums.org/showthread.php?t=126341](http://ubuntuforums.org/showthread.php?t=126341)
[http://ubuntuforums.org/showthread.php?t=137287](http://ubuntuforums.org/showthread.php?t=137287)

Suggestion: modprobe usbkbd
This does not work on Karmic though ([https://help.ubuntu.com/community/BarcodeReaders](https://help.ubuntu.com/community/BarcodeReaders))

---

