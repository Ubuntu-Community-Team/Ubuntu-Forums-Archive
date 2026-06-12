---
title: "brother 8840d"
date: 2012-10-31
forum: Hardware
---

### Post by alenis on 2012-10-31
I have a Brother 8840d printer/scanner, old but still great. Unfortunately I can't use it anymore with the newest Ubuntu (12.04). I installed the drivers following the instructions found in the Brother site, but I cannot print. 
If anybody can help I would be very grateful!


P.S. Why is that each time a new Ubuntu gets out some piece of hardware stops working? It happened with this printer, with a Laserjet 1200 before it, with my Logitech USB webcam which doesn't work anymore with Skype, etc. If Ubuntu/linux has a weak point, it's hardware support. What's the use of a gorgeous desktop if you have to spend a thousand euro to upgrade all your hardware? And they say that one of advantage of Linux is support for old hardware!? I am not surprised that many people stick to Windows, even those who find it terrible.

P.P.S The printer works with parallel conncetion, the scanner doesn't. Downloading Debian :(. Thinking about trying Mint.

---

### Post by pdc on 2012-10-31
Brother now provide an installer script

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr)


......it should save one from following instructions ..

do you want to delete your existing driver and install this as a try?

Ubuntu provide a debugging wiki

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

..... a bit tedious but it might help

---

### Post by alenis on 2012-11-01
Thanks, I will try both possible solutions as soon as possible.

---

### Post by pdc on 2012-11-01
phew; always something new to learn everyday;

when I look at the driver site Brother provide for your printer:

I notice there is a ppd file as well; one can optionally download;

it has instructions:

I note they say 

> ***Note For Ubuntu : Use "/usr/share/ppd" folder instead of "/usr/share/cups/model" folder.

I see my version has ppd files in BOTH places ...... perhaps developers covering both bases.............

you might find this worth a read

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1c.html)

---

### Post by alenis on 2012-11-01
I found this notice on the Brother site:

> 
When you are using the Distribution listed below, you can not scan from the machine connected to a USB port.

Distribution:
    Fedora 15, Fedora 16, openSUSE 11.4, openSUSE 12.1, Mandriva 2011, Ubuntu 11.10,
    and Distribution released after 2012.
Related Models:
    DCP-1000, DCP-1400, DCP-8020, DCP-8025D, DCP-8040, DCP-8045D, FAX-4750e, FAX-5750e, MFC-4800, MFC-6800, MFC-8220, MFC-8420, MFC-8440, MFC-8500, MFC-8820D, MFC-8840D, MFC-9030, MFC-9070, MFC-9160, MFC-9180, MFC-9660, MFC-9700, MFC-9760, MFC-9800, MFC-9860, MFC-9880


and so I must give up Ubuntu, because I need the printer and the scanner to work. But I wonder why the distributions mentioned are no longer capable to handle this device. Maybe something is changed in the management of USB ports. I noticed that, sometimes, transfer to hard disks connected via USB is very slow. This might be a symtpm of something wromg in the usb libraries. Is there a way to keep using Ubuntu 12.04 replacing the new usb libraries with the older ones?

---

### Post by kachilda on 2012-11-01
Ya I'm in the same boat with the brother MFC 9700 scanner drivers not working in Christian Ubuntu 12.04 I got around it by installing Windows 7 in virtual box. Make sure you download the latest one from the Virtual box web sight the one in the Ubuntu repositories needs to be updated and make sure you download and install the virtual box extension pack as well so you can setup and use virtual usb.
let me know if you find a working scan driver for Btorher MFC 9700 in ubuntu 12.04. By the way Windows 7 does not need to be on line in order to install these drivers inside virtual box but you might need to have the installation dvd in the dvd drive. Cheers

[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)
[http://www.dedoimedo.com/computers/virtualbox-usb.html](http://www.dedoimedo.com/computers/virtualbox-usb.html)

---

### Post by kachilda on 2012-11-01
Another off topic link you may enjoy 

[http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/](http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/)

I personally went with the Cinnamon start menu. Check out the link you'll get it.:):guitar:

---

### Post by alenis on 2012-11-02
Unfortunately I badly need the printer and scanner for administrative work, so I (sadly) installed Debian again. Ugly, but working. But I will try the next Ubuntu versions: maybe they will solve the problem (which is not limited to my printer, I see) in the future.
Thanks
Alessandro

---

