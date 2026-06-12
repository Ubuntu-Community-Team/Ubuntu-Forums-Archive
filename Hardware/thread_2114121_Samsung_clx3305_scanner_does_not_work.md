---
title: "Samsung clx3305 scanner does not work"
date: 2013-02-09
forum: Hardware
---

### Post by discnorth on 2013-02-09
Dear all;

I got a very nice Samsung CLX 3305 using USB.

I have been fighting ;-) to install it and has now the printer funcionality working, but the scanner does not want to install.

I have ubuntu 12.04 with latest updates installed.

lsusb: Bus 003 Device 018: ID 04e8:3456 Samsung Electronics Co., Ltd 

if I do sane-find-scanner I get

found USB scanner (vendor=0x0b0c, product=0x0009) at libusb:009:002
found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3456 [CLX-3300 Series]) at libusb:003:018


How can I solve this?

Best regards

---

### Post by dabl on 2013-02-09
Does ```
scanimage -L
``` show it?

---

### Post by ikmailnaarjou on 2013-03-24
Hi there,

I have that printer to bought this weekend: the Samsung clx-3305w.
The installation of the printerdriver was easy for me on lubuntu 12.04.
Even printing over tcp/ip was not a problem.
But the scanner installation is a problem.

scanimage -L say:
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-lsaYky/pkcs11: No such file or directory

I found out that sane is not support the printer completly, but it looks like it should do something:
[http://www.sane-project.org/cgi-bin/driver.pl?manu=samsung&model=&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=samsung&model=&bus=any&v=&p=)

But my problem is: i do not understand what this meens.
How do i get this fixed?

Can sombody point me the way?

Ron

---

### Post by Tx0 on 2013-05-05
Hi there,
I have a Samsung CLX-3305 on Ubuntu 12.04 and the scanner wasn't detected by SANE.

Reading SANE documentation I've noticed that the **xerox_mfp** backend supports some scanners from Samsung.
So I've tried adding the USB device to **/etc/sane.d/xerox_mfp.conf**, like this:

```

$ lsusb | grep Samsung
Bus 002 Device 005: ID 04e8:3456 Samsung Electronics Co., Ltd

```

The relevant field is the ID **04e8:3456**, which must be added as a couple of hexadecimal numbers. So I've done:

```

echo "usb 0x04e8 0x3456" >> /etc/sane.d/xerox_mfp.conf

```

Then I've logged out and logged in again and the scanner worked perfectly with xsane!
I hope this could work for others too.

---

### Post by raulmateos on 2013-05-27
Hello!

I have ubuntu 13.04 64 bits.
I just bought my  CLX-3305W. I downloaded the UnifiedLinuxDriver_CLX-3300_0.86.tar.gz  file. Installed it, and no USB scanner detected, yes the printer. These  are the outputs:

root@linx:/etc/sane.d# lsusb
Bus 007 Device 016: ID 04e8:3456 Samsung Electronics Co., Ltd 
Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam

root@linx:/etc/sane.d# lsmod | grep usb
usblp                  11820  0 

dmesg:

usb 7-1: new high-speed USB device number 18 using ehci-pci
usb 7-1: New USB device found, idVendor=04e8, idProduct=3456
usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 7-1: Product: CLX-3300 Series
usb 7-1: Manufacturer: Samsung Electronics Co., Ltd.
usb 7-1: SerialNumber: Z76JB8KD2B00KHE
usblp 7-1:1.1: usblp0: USB Bidirectional printer dev 18 if 1 alt 0 proto 2 vid 0x04E8 pid 0x3456

root@linx:/etc/sane.d#  Linux linx 3.8-13.dmz.1-liquorix-amd64 #1 ZEN SMP PREEMPT Sun May 12  00:46:08 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

- sane-find-scanner -v returns nothing

I  had a problem installing the UnifiedLinux driver, SANE was not  detected. Checkin the install.sh, I linked the library libsaned.so.1  from /usr/lib/x86_64-linux-gnu/ to /usr/lib64/ and installed it.

Any thought?

Thank you in advance,

Raul

---

