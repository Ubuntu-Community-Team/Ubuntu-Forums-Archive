---
title: "Can't setup HP usb printer"
date: 2013-02-27
forum: Hardware
---

### Post by hillerj on 2013-02-27
Hello, I setup my first Ubuntu server (12.04) recently and things have been going good with only minor issues that is until I started setting up my printer.  It is a HP usb printer and when I hook it up here is what I see in syslog.

Feb 27 21:17:40 myserver kernel: [ 3379.574579] usb 5-2: new full-speed USB device number 2 using xhci_hcd
Feb 27 21:17:40 myserver kernel: [ 3379.660620] usb 5-2: ep 0x82 - rounding interval to 1024 microframes, ep desc says 2040 microframes
Feb 27 21:17:40 myserver mtp-probe: checking bus 5, device 2: "/sys/devices/pci0000:00/0000:00:1c.7/0000:06:00.0/usb5/5-2"
Feb 27 21:17:40 myserver mtp-probe: bus: 5, device: 2 was not an MTP device
Feb 27 21:17:40 myserver udev-configure-printer: add /devices/pci0000:00/0000:00:1c.7/0000:06:00.0/usb5/5-2/5-2:1.0
Feb 27 21:17:40 myserver udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1c.7/0000:06:00.0/usb5/5-2
Feb 27 21:17:40 myserver udev-configure-printer: Device vendor/product is 03F0:0111
Feb 27 21:17:40 myserver kernel: [ 3379.683370] usb 5-2: ep 0x82 - rounding interval to 1024 microframes, ep desc says 2040 microframes
Feb 27 21:17:40 myserver kernel: [ 3379.686866] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 3 vid 0x03F0 pid 0x0111
Feb 27 21:17:40 myserver kernel: [ 3379.686884] usbcore: registered new interface driver usblp
Feb 27 21:17:40 myserver udev-configure-printer: add /devices/pci0000:00/0000:00:1c.7/0000:06:00.0/usb5/5-2/5-2:1.0/usb/lp0
Feb 27 21:17:40 myserver kernel: [ 3379.873827] hub 4-0:1.0: unable to enumerate USB device on port 2
Feb 27 21:17:40 myserver udev-configure-printer: failed to claim interface
Feb 27 21:17:40 myserver udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1c.7/0000:06:00.0/usb5/5-2
Feb 27 21:17:40 myserver udev-configure-printer: MFG:Hewlett-Packard MDL:OfficeJet G55xi SERN:SGA9B10H54VL serial:SGA9B10H54VL
Feb 27 21:17:41 myserver udev-configure-printer: no corresponding CUPS device found


But when I do lsusb I see:

Bus 005 Device 002: ID 03f0:0111 Hewlett-Packard G55xi Printer/Scanner/Copier


I tried to add the printer in CUPS but of course it doesn't list it.  Being new to this I am not really sure where to go from here.

Any help is appreciated!

---

### Post by fdrake on 2013-02-27
first you can start by telling us what kind of printer you have then install these updates and check if it helps installling the printer:
```

sudo apt-get install printer-driver-hpcups hplip-cups
sudo apt-get upgrade && sudo apt-get update

```

also give us the the kernle info
```

uname -a

```
plug your printer and attach as a txt file the output of:
```

lsusb -vvv

```

---

### Post by foresthill on 2013-02-27
Looks like one of those all-in-one units. Not all of them are supported yet by HP, unfortunately.

---

### Post by hillerj on 2013-02-27
Here is the output to uname -a:

Linux myserver 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Also, I attached the output of lsusb but the full output of the command exceeded the max attachment size.  I pulled out just the information on the printer but let me know if you need more information from that command.

I installed the packages you suggested but that did not help.  Although, should I reboot after doing that install and then try?

Thank you for the reply.

---

### Post by hillerj on 2013-02-28
Any other thoughts on this?  I tried it on my Ubuntu desktop machine as well but got the same results.  I don't need the scanner to work just the printer.  Is there any generic driver I can use?

---

### Post by hillerj on 2013-03-02
Well I feel like I have gotten closer to getting this OfficeJet G55xi setup but I still can't get it to print.  When I looked at the hplip site it looks to be supported.  See here -> [http://hplipopensource.com/hplip-web/models/officejet/officejet_g55xi.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_g55xi.html).  I downloaded hplip from the same site and followed the installation instructions.  Now I can add the printer (actually the HP software adds it for me when I turn the printer on).  However, when I try and print it does't work.  Attached is what I see in syslog when I connect the printer and when I try and print a test page.  I see some errors in there but I don't know what to make of them.  I have rebooted many times just in case as well as deleting the printer and re-adding it.  Please help!  Thanks.

---

