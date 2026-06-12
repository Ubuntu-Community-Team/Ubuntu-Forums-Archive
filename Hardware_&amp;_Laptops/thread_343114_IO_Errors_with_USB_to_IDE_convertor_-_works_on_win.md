---
title: "I/O Errors with USB to IDE convertor - works on windows"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by grahams on 2007-01-20
I just picked up a USB to IDE converter called the R-Driver II. I want to use it to connect bare IDE devices via USB ports.  Unfortunately I can not get it to work on ubuntu 6.10, but it works on Win/XP. 

scanning with lsusb and lsscsi my system detects the device and a /dev/sda is created. However the disk partitions aren't seen and I can't mount it. A simple od </dev/sda fails with I/O errors usually immediately but sometimes after reading a few disk blocks. 
I also tried booting from a live 6.06 cd and I see the same errors. I've successfully accessed the same disk from the same machine via windows XP without errors. 

I'm guessing this is an interoperability issue with the Ubuntu USB driver. From the website at [http://www.usbgeek.com/prod_detail.php?prod_id=0190](http://www.usbgeek.com/prod_detail.php?prod_id=0190) the chipset is a MYSON CENTURY, CS88186

Is anyone aware of a work around for this?

Many thanks

---

### Post by grahams on 2007-01-22
I just booted from a Knoppix LIVE CD and I can access disks attached to the USB to IDE converter. 

On knoppix a lsmod |grep usb show that usb_storage, usb_ohci and usbcore loaded.

After rebooting ubuntu 6.10 an lsmod sees usb_storage and usbcore but not usb_ohci. A modprobe usb_ohci fails with module not found.

Anyone know if this is an issue on 2.6 kernels (Knoppix is 2.4)?

---

### Post by IntuitiveNipple on 2007-01-22
I've not come across your problem but I recall recently reading about changes to the usb modules in 2.6.x.

On Edgy I see:
```
$ lsmod | grep usb
usb_storage            75072  2 
scsi_mod              144648  4 sbp2,sg,sd_mod,usb_storage
libusual               17040  1 usb_storage
usbhid                 45152  0 
usbcore               134912  12 snd_usb_audio,snd_usb_lib,ipaq,usbserial,usblp,ov51x,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
```
Note the two modules **ehci_hcd** (Enhanced OHC) and **ohci_hcd** (OHC). I recall that the former is for USB v2 devices and the latter for older USB v1/1.1 devices.

Try loading one of those and see if you make progress.

---

### Post by grahams on 2007-01-22
Thanks

Here is my lsmod output. Those modules are loaded, by default apart from orinoco_usb (the converter also doesn't work on another system on ubuntu that doesn't have an orinoco card).

$ lsmod |grep usb
usb_storage            75072  0 
scsi_mod              144648  4 libata,sg,sd_mod,usb_storage
libusual               17040  1 usb_storage
orinoco_usb            22284  0 
orinoco                48148  1 orinoco_usb
usbcore               134912  6 usb_storage,libusual,orinoco_usb,ehci_hcd,ohci_hcd

I don't see anything on launchpad that fits my issue. Maybe I need to submit a bug report.

---

### Post by grahams on 2007-01-22
I just tried booting a slax live cd which uses a 2.6 kernel (2.6.16) and it like ubuntu can not access discs via this converter. Looks like a much bigger issue.

---

### Post by grahams on 2007-05-27
This issue is fixed in the 2.6.20-15 kernel

---

