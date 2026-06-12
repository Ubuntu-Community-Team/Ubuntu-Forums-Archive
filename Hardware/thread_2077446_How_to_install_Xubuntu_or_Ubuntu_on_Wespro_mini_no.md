---
title: "How to install Xubuntu or Ubuntu on Wespro mini notebook"
date: 2012-10-28
forum: Hardware
---

### Post by arifalisyed on 2012-10-28
Hi,
   My brother has a Wespro n720 mini notebook laptop.
its comes Windows CE pre-installed.

1=>It doesn't have any CD Drive
2=>It has Wifi connectivity, USB port, Ethernet port.
3=>It has WMT ARM WM8505 processor
4=>It has only 128 MB RAM and 2 GB hard disk
5=>I have a Pen Drive of 8GB
6=> I could really not find any option to enter into BIOS,
Tried pressing F1 to F12 and Del key after powering on.
7=> I have a dialup USB modem internet, EV-DO modem ( which works well with my Xubuntu desktop)
8=> I do not know which motherboard it is :( 

provided all these facts, I want to know if I can install Xubuntu ( preferred) or Ubuntu on this so far useless device "wespro".


I see on this page [https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM) 
that i Ubuntu has been ported for ARM processors.

But I am not sure about which distribition should I go for?
a) OMAP b)Tegra (AC100) c) IMX53 d) ARM Server

Another thing is since I was never able to get into BIOS, I do not know if there is any option to boot from USB stick, I can get to know that only after I plug-in a bootable USB device.

Can anyone help me with
1) which ARM image to go far?
2) Any step by step guide to install *buntu on ARM device?
3) Have anyone ever tried installing *Buntu on Wespro device?

Thanks in advnace.

---

### Post by arifalisyed on 2012-10-28
oh oh ... i dont find my device in the list.

[https://wiki.ubuntu.com/ARM/DeviceSupport](https://wiki.ubuntu.com/ARM/DeviceSupport)

So looks like If I am able to make it, I  will be first on earth to run ubuntu on Wepro mini notebook device.

---

### Post by angry_johnnie on 2012-10-29
Whether or not you will be able to install linux on that machine directly, depends on whether or not it has a NAND flash drive.

Some do, some don't.  It's random, really.

When they don't, what they have is really just a usb stick soldered on to the motherboard.

You can't install linux like that.  Attempting to do so will brick your device.

If you don't know whether your device has a NAND flash drive, and don't want to dissassemble it just to find out, there is another approach.

Go to Bento Linux:

[http://bentolinux.org/downloads](http://bentolinux.org/downloads)

Get the debian image.

You'll need a SD card with 2 partitions:

1 fat32 partition (about 100 mb)
1 ext2 partition (remaining space)

Extract the "fatpart" files on the fat partition, and the "extpart" on the ext2 partition.

Insert sd into device and power on.  It will boot into a working Debian system.

That's it. :)

I can confirm it works.  BUT it works only on the wm8505.  If that's what you have, you're ok.

I installed Debian 5 on mine, and successfuly upgraded to Debian 6.  You'll need to use oss for sound, and fbdev for display.  Everything works, even wifi.  Mine uses rt3070sta wifi driver.  Yours may be different.  Look it up.

Here's a screenshot:

[http://ubuntuforums.org/attachment.php?attachmentid=223576&d=1346641735](http://ubuntuforums.org/attachment.php?attachmentid=223576&d=1346641735)

Here's the Bento Linux wiki:

[http://bentolinux.org/wiki/debian](http://bentolinux.org/wiki/debian)

---

### Post by arifalisyed on 2012-10-29
> **angry_johnnie said:**
> Whether or not you will be able to install linux on that machine directly, depends on whether or not it has a NAND flash drive.

Some do, some don't.  It's random, really.




its spec says it has NAND flash drive

[http://chandigarhcity.olx.in/wespro-7-inches-netbook-n-720-mini-laptop-with-wifi-cheapest-price-anywhere-iid-241166114](http://chandigarhcity.olx.in/wespro-7-inches-netbook-n-720-mini-laptop-with-wifi-cheapest-price-anywhere-iid-241166114)


I guess it has a port for inserting SD card as well. 
Should try your method and let you know. thanks a lot.

First i want to get rid of Windows CE and then later on i can attempt to install any ubuntu.

---

### Post by angry_johnnie on 2012-10-29
> **arifalisyed said:**
> its spec says it has NAND flash drive


Yeah, that's the tricky part.  It's pretty misleading, as they all claim to have a NAND flash drive, but that's not always true.  Mine said NAND flash with big bold letters on the box itself, and it was still a usb stick soldered on the motherboard, instead.

The only way to find out is to dissassemble it :)

Good luck!

---

### Post by gordintoronto on 2012-10-29
In any case, it doesn't have enough memory to run a full-featured Linux. Maybe Android.

---

### Post by angry_johnnie on 2012-10-30
> **gordintoronto said:**
> In any case, it doesn't have enough memory to run a full-featured Linux. Maybe Android.

Debian's as full-featured as they get, and it works.  I guess it depends on how you define "full-featured."  If you're thinking HD video and 3D games, then no, it can't do that with either windows, linux, or android.

However, Debian performs much faster, and can do much more, given the limited resources.  Windows CE, on the other hand, is useless.

---

### Post by Parker32 on 2012-10-31
Thanks to describe all path.

---

### Post by yuwash on 2013-02-08
Hello, I also have a similar device (but Android 2.2 installed) that is named Jay-tech Netbook U9903H with Infotmic iMAPx210 1 GHz processor. Since it doesn't react on several attempts of booting from SD card, I connected the device with an ubuntu machine with usb. dmesg says (excerpt)

[LIST]
[*]usb 3-1: >new full-speed USB device number 6 using ohci_hcd
[*]usb 3-1: >New USB device found, idVendor=18d1, idProduct=dead
[*]usb 3-1: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
[*]usb 3-1: >Product: wwe
[*]usb 3-1: >Manufacturer: infotmic
[*]usb 3-1: >SerialNumber: 0000
[*]scsi5 : usb-storage 3-1:1.0
[/LIST]
Though a mass storage device is recognized, no partition can be found or the drive accessed with fdisk.

BTW at [http://netbook.poodwaddle.com/](http://netbook.poodwaddle.com/) you can get Android files for flashing (to be put on SD card? I haven't tried yet)

---

