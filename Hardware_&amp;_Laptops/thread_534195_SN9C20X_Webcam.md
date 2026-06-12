---
title: "SN9C20X Webcam"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by abhaysahai on 2007-08-24
Hi ,
I have a sonix chipset based webcam with the following details as per lsusb

Bus 004 Device 002: ID 0c45:6270 Microdia

I went through the usual [http://www.linux-projects.org/modules/mydownloads/](http://www.linux-projects.org/modules/mydownloads/) and tried making the driver work for me. However I get a dmesg error :: 

[ 853.097767] sn9c20x: V4Lx driver for SN9C20x PC Camera Controllers v2:2.05
[ 853.097773] sn9c20x: (C) 2007 Luca Risolia
[ 853.097775] sn9c20x: By using this software, you declare that you have read and accepted the LICENSE included in the 'copyright' file accompanying this software.If not, stop using this software.
[ 853.150770] usb 4-2: SN9C20X PC Camera Controller detected (vid 0x0C45)
[ 853.175433] usb 4-2: Sorry, your webcam is not supported at the moment.
[ 853.175441] usb 4-2: For more informations, please send an email to the author: <luca.risolia@studio.unibo.it> , together with the output of the command 'lsusb -v' and, if possible, a link to the reseller
[ 853.176291] usbcore: registered new interface driver sn9c20x

I understand that the current driver will not work with my webcam. 

I went ahead and created a[ launchpad bug]("https://bugs.launchpad.net/ubuntu/+bug/131733") 

looks like not many devs care about this webcam, as this bug was created on 
2007-08-11 and yet it is new and not assigned to anyone. 

Here we have a situation where I cannot use one of my hardware device  which works perfectly in Windows and there appears no solution in near future. 
Hence every time I have to video chat with anyone I hook up the webcam to windows XP  laptop.

---

