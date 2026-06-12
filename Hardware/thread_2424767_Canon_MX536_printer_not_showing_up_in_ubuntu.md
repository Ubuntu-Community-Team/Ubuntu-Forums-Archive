---
title: "Canon MX536 printer not showing up in ubuntu"
date: 2019-08-14
forum: Hardware
---

### Post by swangnation on 2019-08-14
Hi guys,

I'm still new to ubuntu but i simply didn't realize what a mission it would be to get ubuntu 18.04 to recognize my canon MX536 printer. I working off a Asus X55E AMD laptop.

I've turned my printer on THEN plugged it into the laptop via usb.

when i ```
lsusb
``` i get the following output

```
Bus 002 Device 002: ID 0bda:5606 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

when i ```
/usr/sbin/lpinfo -v
``` i get the following output

```
network socket
network ipps
network ipp
network lpd
network beh
network http
network https
file cups-brf:/
direct hp
direct hpfax
```

I have downloaded the necessary drivers ( 6 in total but i probably only need a few of those ) for this printer and this question may sound silly but is there any particular order in which i have to install these drivers? That's assuming that they are going to work.

I did some googling and i saw some instances where you have to force the architecture which means....something. So i thought i would ask here first.

I just want to to configure this ubuntu to recognize my printer so i can get the functions to work.

Any help would be greatly appreciated. Thank you in advance too!

---

### Post by him610 on 2019-08-14
> I've turned my printer on THEN plugged it into the laptop via usb.
Try plugging it in, turning it on, then starting your computer. It may help with recognition.
Not familiar with Canon printers, or USB-connected printers. With that said, most printer installations are similar. On this Canon website, [https://www.canon.com.au/printers/pixma-mx536/support]("https://www.canon.com.au/printers/pixma-mx536/support"), there are two downloads (Debian) for your machine - one for printer and one for scanner. 
Download both packages,
MX530 series IJ Printer Driver Ver. 4.10 for Linux (debian Packagearchive)
MX530 series ScanGear MP Ver. 2.30 for Linux (debian Packagearchive)

Follow the instructions provided by Canon to install printer then scanner.
Good luck.

---

### Post by &amp;wP*!) on 2019-08-14
Copy-paste the part of the file /var/log/syslog which shows the messages from the operating system when you plug-in your printer into the USB port. 
You can use [http://pastebin.com](http://pastebin.com) to copy-paste.

---

### Post by brian_p on 2019-08-15
*lsusb* does not show the device. There is zero chance of USB printing until this is sorted.

---

### Post by him610 on 2019-08-15
> lsusb does not show the device.
Sometimes it takes awhile.

---

### Post by brian_p on 2019-08-15
> **him610 said:**
> Sometimes it takes awhile.

Like a day?

---

