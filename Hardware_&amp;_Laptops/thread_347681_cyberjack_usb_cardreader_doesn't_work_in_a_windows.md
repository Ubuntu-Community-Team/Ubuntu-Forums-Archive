---
title: "cyberjack usb cardreader doesn't work in a windows xp virtual machine"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by chriss on 2007-01-27
Hi,

on ubuntu 6.10 i installed VMware server. There i installed a win xp professional virtual machine.

The cyberJack e-com chipcardreader is plugged in with USB. I installed the driver provided from [www.reiner-sct.de](www.reiner-sct.de), the manufacturer.

As you can see, the kernel modules are running:

chris@ubuntu:~$ lsmod |grep cyberjack 
cyberjack              10244  0 
usbserial              32616  1 cyberjack 
usbcore               130304  5 cyberjack,usbserial,ehci_hcd,ohci_hcd

In the VMware GUI in VM/Removable Devices/USB Devices nothing appears. I can see only "Empty" there in.

What do i have to do that the cardreader reaches the virtual machine in vmware?

Thanks for your ideas.

chriss

---

### Post by chriss on 2007-01-29
Here the How-To:

Shutdown the VM

VM --> Settings --> Add --> USB Controller --> Next --> Finish

When you power on your VM you can plug USB devices with VM --> Removeable Devices --> USB Devices.

Thats it :-)

chriss

---

