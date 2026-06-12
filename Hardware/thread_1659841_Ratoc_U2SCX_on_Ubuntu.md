---
title: "Ratoc U2SCX on Ubuntu"
date: 2011-01-04
forum: Hardware
---

### Post by txapelgorri on 2011-01-04
Hi there:

I'm looking for some hint on getting running this piece of hardware:

[http://www.ratocsystems.com/english/products/U2SCX.html](http://www.ratocsystems.com/english/products/U2SCX.html)

Seems to work (or used to be) as seen in here:

[http://www.ratocsystems.com/english/download/driver/linux/u2scx.html](http://www.ratocsystems.com/english/download/driver/linux/u2scx.html)

But when I plug it the only response I get is:

```
tail /var/log/syslog
...
kernel: [16622.800126] usb 1-1: new high speed USB device using ehci_hcd and address 13
...

```

I've attach a SCSI Scanner at the other side (HP Scanjet 5P), but I get no more info from the kernel.

I'm using 32bits Ubuntu Maverick.

I found also some other people at Italy who tried to configure it out, and with Mandriva 2009 they get more feedback from the USB-SCSI adaptor:

[http://www.linux-magazine.it/forum/index.php/topic,1562.msg9061.html#msg9061](http://www.linux-magazine.it/forum/index.php/topic,1562.msg9061.html#msg9061)

Any help on this?

Thanks in advance, Ibon.

---

### Post by andre_renaud on 2011-02-08
I've also got a couple of these units. They do work under Linux (Ubuntu 10.04), however you need a windows machine to change them into 'mass storage mode'. Once in this mode I was able to access a tape device on the SCSI bus successfully, using the standard 'st' Linux scsi tape driver.

Here is the response I got from Ratoc support:
----
Thank you for using our product.

Please make sure to change the U2SCX into the "mass storage mode"  before using it with unix PC. You will need to run the configuration utility on either WIndows or MacOS to change the mode.

The following modules should be loaded.


> kernel: usb 2-4: new high speed USB device using ehci_hcd and address 8 
> kernel: usb 2-4: configuration #1 chosen from 1 choice 
> kernel: usb 2-4: New USB device found, idVendor=0584, idProduct=0220 
> kernel: usb 2-4: New USB device strings: Mfr=1, Product=3, SerialNumber=2 
> kernel: usb 2-4: Product: USB-SCSI Converter 
> kernel: usb 2-4: Manufacturer: RATOCSystems,Inc. 
> kernel: usb 2-4: SerialNumber: xxxxxx000007 
> kernel: Initializing USB Mass Storage driver... 
> kernel: scsi6 : SCSI emulation for USB Mass Storage devices 
> kernel: usbcore: registered new interface driver usb-storage 
> kernel: USB Mass Storage support registered. 
> kernel: scsi 6:0:0:0: Processor HP C2520A 
> 3503 PQ: 0 ANSI: 2 
> kernel: scsi 6:0:0:0: Attached scsi generic sg2 type 3 
-----------------

Hope that helps,
Andre

---

### Post by txapelgorri on 2011-02-10
Hi Andre:

Yes, you are absolutely right. I finally get in touch with supporting contact at [www.rexpccard.co.jp](www.rexpccard.co.jp) and they suggested me the same: turn on "Mass storage" mode. I did and finally I get this device work :)

Thanks a lot, Ibon.

---

