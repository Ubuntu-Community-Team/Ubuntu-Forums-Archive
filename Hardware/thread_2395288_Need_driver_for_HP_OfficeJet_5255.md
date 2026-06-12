---
title: "Need driver for HP OfficeJet 5255"
date: 2018-06-29
forum: Hardware
---

### Post by bper on 2018-06-29
hello,

I'm running 16.04 LTS 64-bit. I tried to add an HP OfficeJet 5255 MFP. The driver that is suggested by the Add Printer option is the openprinting-gutenprint driver. When it attempts to install the driver, the install hangs. 

Can anyone suggest a driver that will work?

Thanks

---

### Post by ajgreeny on 2018-06-29
Looking at the hplip page of supported Officejet printers [https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index) I cannot find that specific version but there are may other versions of Officejet that are fully supported.
Make sure you have hplip and hplip-gui installed then open hplip-toolbox and try installing the printer from that.

I will be very surprised if you can not get it to work as most HP printers are very well, and fully supported by hplip.

---

### Post by bper on 2018-07-07
Thanks,

I installed hplip and hplip-gui. When I run setup, it doesn't see the device. It states no devices found. It is connected via usb port. I restarted the computer and restarted the printer, and it is still not discovered.

---

### Post by Autodave on 2018-07-07
Have you tried another USB cable?  You could also try booting the PC *after* the printer is turned on and ready.

---

