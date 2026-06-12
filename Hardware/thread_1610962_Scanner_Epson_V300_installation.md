---
title: "Scanner Epson V300 installation"
date: 2010-11-01
forum: Hardware
---

### Post by hibou107 on 2010-11-01
Hi, I have Ubuntu 10.10 version
I have a Epsion V300, I have installed the image scan! and also the iscan package

[LIST]
[*]iscan 2.26.0-3.ltdl7
[*]iscan data 1.4.0-1
[*]esci-interpreter-gt-f720
Plugin for the GT-F720/S620 and Perfection V30/V300
[/LIST]
But when I launch Image! Scan, the error is
> Could not send information to scannerSo I try to go on with the tutorial in the avasys website
When I try to read the [document]("javascript:Dl_File('S000000276');")

> 1. run sane-find-scanner to find the USB connection
$ sane-find-scanner | grep 0x04b8
found USB scanner (vendor=0x04b8,
product=0x0110) at libusb:001:002
From the sample output above the USB connection is at 001/002.
2. change the permissions with
Of course, replace the numbers with those you found in step 1.
Note that you will have to do this every time you (re)connect or power
cycle your USB scanner or reboot your computer.
If you want to check whether you are using libusb, just have a look at
the /etc/sane.d/epkowa.conf configuration file. It should have
an
usb
line (without a leading &#8216;#&#8217;). Specifically, the
# usb /dev/usb/scanner0
line (and the lines like it) should all start with a &#8216;#&#8217;.
When I type
> # chmod 0666 /proc/bus/usb/001/009
The error is
> chmod: cannot access `/proc/bus/usb/001/009': No such file or directory
Can you have solution for me?
Thanks

---

### Post by IcarusR on 2010-11-01
Did you try running as root ?

```
sudo chmod 0666 /proc/bus/usb/001/009 
```

---

### Post by hibou107 on 2010-11-01
> **IcarusR said:**
> Did you try running as root ?

```
sudo chmod 0666 /proc/bus/usb/001/009 
```

Hi,
this is something very stupid, I've just need to restart and then turn off and on the scanner and now that works
Thanks for your help

---

