---
title: "Express card - rs232"
date: 2008-05-05
forum: Hardware
---

### Post by mputin on 2008-05-05
Hi

Hoping someone can help me get an RS232 express card driver for 7.10. The card itself is just a cheapy so Id be thinking a generic driver might do the job. There is no information on the website I have got regarding chipsets for it.

The laptop is an ASUS PRO31JR.

It installs fine under Windows so I can provide the Windows driver details if it'll help.

lsusb output:

Bus 005 Device 004: ID 13fe:1a00  
Bus 005 Device 003: ID 0c45:624f Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 007: ID 9710:7710 MosChip Semiconductor 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c019 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

It is the MosChip Semiconductor. 

Im really not sure where to go from here.

Thanks in advance.

---

### Post by mputin on 2008-05-06
So I think I am getting closer to solving the issue. 

I did this:

sudo insmod `modprobe -l | grep usbserial`

to insert the USB to serial module into the kernel.

Then, when I did dmesg I was able to see this:
--CUT--
[ 1762.564000] usbcore: registered new interface driver usbserial
[ 1762.564000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 1762.564000] usbcore: registered new interface driver usbserial_generic
[ 1762.564000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 1777.684000] usb 4-1: USB disconnect, address 4
[ 1780.096000] usb 4-1: new full speed USB device using uhci_hcd and address 5
[ 1780.248000] usb 4-1: configuration #1 chosen from 1 choice
[ 3787.712000] usb 4-1: USB disconnect, address 5
[ 3873.532000] usb 4-1: new full speed USB device using uhci_hcd and address 6
[ 3873.684000] usb 4-1: configuration #1 chosen from 1 choice
[ 3874.036000] usb 4-1: USB disconnect, address 6
[ 3875.032000] usb 4-1: new full speed USB device using uhci_hcd and address 7
[ 3875.184000] usb 4-1: configuration #1 chosen from 1 choice
[ 3880.840000] usb 4-1: USB disconnect, address 7
[ 3884.492000] usb 4-1: new full speed USB device using uhci_hcd and address 8
[ 3884.644000] usb 4-1: configuration #1 chosen from 1 choice
[ 4122.856000] usb 4-1: USB disconnect, address 8
[ 4127.948000] usb 4-1: new full speed USB device using uhci_hcd and address 9
[ 4128.100000] usb 4-1: configuration #1 chosen from 1 choice

So, to confirm I did:

sudo udevmonitor

Which shows this when I pull the card out and put it back in:
UEVENT[1210052008.900134] remove   /class/usb_endpoint/usbdev4.9_ep85 (usb_endpoint)
UEVENT[1210052008.900228] remove   /class/usb_endpoint/usbdev4.9_ep06 (usb_endpoint)
UEVENT[1210052008.900265] remove   /class/usb_endpoint/usbdev4.9_ep87 (usb_endpoint)
UEVENT[1210052008.900301] remove   /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0 (usb)
UEVENT[1210052008.900336] remove   /class/usb_device/usbdev4.9 (usb_device)
UEVENT[1210052008.900371] remove   /class/usb_endpoint/usbdev4.9_ep00 (usb_endpoint)
UEVENT[1210052008.900405] remove   /devices/pci0000:00/0000:00:1d.3/usb4/4-1 (usb)
UDEV  [1210052008.902848] remove   /class/usb_endpoint/usbdev4.9_ep85 (usb_endpoint)
UDEV  [1210052008.903600] remove   /class/usb_endpoint/usbdev4.9_ep06 (usb_endpoint)
UDEV  [1210052008.908379] remove   /class/usb_endpoint/usbdev4.9_ep87 (usb_endpoint)
UDEV  [1210052008.908473] remove   /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0 (usb)
UDEV  [1210052008.908513] remove   /devices/pci0000:00/0000:00:1d.3/usb4/4-1 (usb)
UDEV  [1210052008.908551] remove   /class/usb_device/usbdev4.9 (usb_device)
UDEV  [1210052008.908587] remove   /class/usb_endpoint/usbdev4.9_ep00 (usb_endpoint)
UEVENT[1210052011.774188] add      /devices/pci0000:00/0000:00:1d.3/usb4/4-1 (usb)
UEVENT[1210052011.774230] add      /class/usb_endpoint/usbdev4.11_ep00 (usb_endpoint)
UEVENT[1210052011.777173] add      /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0 (usb)
UEVENT[1210052011.777246] add      /class/usb_endpoint/usbdev4.11_ep85 (usb_endpoint)
UEVENT[1210052011.777283] add      /class/usb_endpoint/usbdev4.11_ep06 (usb_endpoint)
UEVENT[1210052011.777318] add      /class/usb_endpoint/usbdev4.11_ep87 (usb_endpoint)
UEVENT[1210052011.777352] add      /class/usb_device/usbdev4.11 (usb_device)
UDEV  [1210052011.787587] add      /devices/pci0000:00/0000:00:1d.3/usb4/4-1 (usb)
UDEV  [1210052011.787619] add      /class/usb_endpoint/usbdev4.11_ep00 (usb_endpoint)
UDEV  [1210052011.827575] add      /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0 (usb)
UDEV  [1210052011.827659] add      /class/usb_endpoint/usbdev4.11_ep85 (usb_endpoint)
UDEV  [1210052011.827697] add      /class/usb_endpoint/usbdev4.11_ep06 (usb_endpoint)
UDEV  [1210052011.827733] add      /class/usb_endpoint/usbdev4.11_ep87 (usb_endpoint)
UDEV  [1210052011.846591] add      /class/usb_device/usbdev4.11 (usb_device)

So, I think Im getting close. BUT, I still cant get it to work. It has been suggested I need somehow "map" usbdev4.9 to /dev/ttyUSB but I dont have that file or know how to do it? Any ideas?

Thanks

---

### Post by mputin on 2008-05-09
Anybody got anything for me?

How about the command:

mknod /dev/ttyUSB0 c 188 0

Can anyone explain this to me? Yes I have looked at the man pages for mknod and even googled it (thats how I found it...) In particular, the "188 0" in the example. I dont know what that means or where those numbers are derived from. The rest Iv got some idea on....

Am I even on the right track?

Anything would be better than nothing....

Thanks

---

### Post by mputin on 2008-05-21
Anybody wanna have a crack at this one?

---

### Post by tarsius4 on 2008-08-09
Did you check for a driver on the Moschip website?

[http://www.moschip.com/html/download_drivers.html](http://www.moschip.com/html/download_drivers.html)

I think you might have the MCS7820 because I did a search for ExpressCard and found this:

[http://www.google.com/search?q=expresscard&btnG=Google+Search&domains=http%3A%2F%2Fwww.moschip.com&sitesearch=http%3A%2F%2Fwww.moschip.com](http://www.google.com/search?q=expresscard&btnG=Google+Search&domains=http%3A%2F%2Fwww.moschip.com&sitesearch=http%3A%2F%2Fwww.moschip.com)

Note that the comment about Express Card applications is in a document about the MCS7820.  I am currently trying to compile the Moschip driver for MCS7715 but I'm having problems.  Run "sudo make" and let me know how it goes.

Steve

---

