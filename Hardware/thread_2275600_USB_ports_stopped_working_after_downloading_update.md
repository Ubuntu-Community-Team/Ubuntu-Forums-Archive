---
title: "USB ports stopped working after downloading updates"
date: 2015-04-27
forum: Hardware
---

### Post by inflameswetrust on 2015-04-27
Hello! In advance, I would like to thank everybody for any help, because I'm starting to get crazy with all this... It took me nearly three months to get this thing rolling like I wanted, and now, i'm helpless even after searching for hours. 

I'm using Ubuntu 14.04 on Acer Aspire E1-532. After todays update, all my USB ports stopped working. Mouse, printer, scanner, flash drive, nothing is recognized. 
After half an hour the problem was briefly fixed, I unbinded and binded one port, and everything came to life. 

So, I did this:

> echo -n "0000:00:14.0" | sudo tee /sys/bus/pci/drivers/xhci_hcd/unbind
echo -n "0000:00:14.0" | sudo tee /sys/bus/pci/drivers/xhci_hcd/bind

However, after rebooting, they stopped working again. So I tried it again. And it worked. But, every time I reboot, my USB ports don't work. Obviously, it's not a hardware issue. 

After typing lsusb command in Terminal, this is what I get

> 

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04f2:b3f6 Chicony Electronics Co., Ltd 
Bus 002 Device 006: ID 0489:e078 Foxconn / Hon Hai 
Bus 002 Device 002: ID 093a:2521 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




Lsusb tree says this

> 
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/8p, 480M
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 5: Dev 6, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 5: Dev 6, If 1, Class=Wireless, Driver=btusb, 12M
    |__ Port 8: Dev 4, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 8: Dev 4, If 1, Class=Video, Driver=uvcvideo, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M




I'm sorry if there is already a solution to my problem, but I've been searching for it for the last 4 hours, and except unbind/bind, I've found nothing helpful.

---

### Post by dino99 on 2015-04-27
im not sure they are the magical commands in your case, but run:

sudo update-pciids
sudo update-usbids

and glance at your logs ( /var/log/ ) to find something usefull (warnings/errors)  (dmesg/syslog)

---

### Post by jeremy31 on 2015-04-27
I have a wild idea
```
echo "blacklist ath3k" | sudo tee /etc/modprobe.d/bt.conf
``````
echo "blacklist btusb" | sudo tee -a /etc/modprobe.d/bt.conf
```

Reboot, downside is that bluetooth won't work unless you modprobe ath3k and btusb later

---

