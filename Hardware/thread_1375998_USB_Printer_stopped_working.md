---
title: "USB Printer stopped working"
date: 2010-01-08
forum: Hardware
---

### Post by lsutiger on 2010-01-08
I have an HP Laser Jet 1020 that I have been using for several months with no problem. It started not to work a couple of days ago. I have changed the cable, which did not do alleviate the problem. 

I tried changing the USB ports. Here is the output from dmesg:
```
 usb 2-3: new full speed USB device using ohci_hcd and address 4
 usb 2-3: device descriptor read/64, error -110
```

I restarted both the computer and printer and then received this:
```
[16073.669026] usb 1-2: new high speed USB device using ehci_hcd and address 14
 usb 1-2: configuration #1 chosen from 1 choice
 usblp0: USB Bidirectional printer dev 14 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2B17
 usblp0: removed
 ppdev0: registered pardevice
 ppdev0: unregistered pardevice

```

Still does not work. I have a network printer setup also. When I try to print to the network printer, the job confirms as sent, but never prints. Others can print to the network printer, as I used to be able to print to the network printer. 

All printers are listed in CUPS.

What should I try next?

---

### Post by desmondo on 2010-01-18
My hp LaserJet 1012 has also mysteriously stopped working.

**Update - fixed**

Per [this thread]("http://ubuntuforums.org/showthread.php?t=1298689"), I reinstalled cups, cups-client, and hplip, and now it's mysteriously working again.

---

### Post by lsutiger on 2010-01-18
Hmm...well, I was having other failures on the motherboard, so I upgraded everything. But I have yet to test the printer, as we have a really good network printer here.

---

