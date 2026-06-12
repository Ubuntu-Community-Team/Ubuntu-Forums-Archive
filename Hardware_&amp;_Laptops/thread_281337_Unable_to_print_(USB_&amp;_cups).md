---
title: "Unable to print (USB &amp; cups)"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by McHenry on 2006-10-20
am trying to get my LaserJet working on my laptop via a usb to parallel cable.

Cups detects the printer correctly and I am able to install it and print test pages etc. The the printer ceases to function and the log is filled with the following messages:

Oct 21 10:11:29 laptop kernel: [17181332.488000] usb 1-1: new full speed USB device using uhci_hcd and address 80
Oct 21 10:11:30 laptop kernel: [17181332.632000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 80 if 0 alt 0 proto 2 vid 0x4348 pid 0x5584
Oct 21 10:11:30 laptop kernel: [17181332.796000] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -84
Oct 21 10:11:30 laptop kernel: [17181333.004000] usb 1-1: USB disconnect, address 80
Oct 21 10:11:30 laptop kernel: [17181333.004000] drivers/usb/class/usblp.c: usblp0: removed
Oct 21 10:11:32 laptop kernel: [17181334.756000] usb 1-1: new full speed USB device using uhci_hcd and address 81
Oct 21 10:11:32 laptop kernel: [17181334.900000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 81 if 0 alt 0 proto 2 vid 0x4348 pid 0x5584
Oct 21 10:11:32 laptop kernel: [17181335.272000] usb 1-1: USB disconnect, address 81
Oct 21 10:11:32 laptop kernel: [17181335.272000] drivers/usb/class/usblp.c: usblp0: removed
Oct 21 10:11:34 laptop kernel: [17181337.024000] usb 1-1: new full speed USB device using uhci_hcd and address 82
Oct 21 10:11:34 laptop kernel: [17181337.168000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 82 if 0 alt 0 proto 2 vid 0x4348 pid 0x5584
Oct 21 10:11:34 laptop kernel: [17181337.332000] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -84
Oct 21 10:11:34 laptop kernel: [17181337.540000] usb 1-1: USB disconnect, address 82
Oct 21 10:11:34 laptop kernel: [17181337.540000] drivers/usb/class/usblp.c: usblp0: removed
Oct 21 10:11:36 laptop kernel: [17181339.292000] usb 1-1: new full speed USB device using uhci_hcd and address 83
Oct 21 10:11:36 laptop kernel: [17181339.436000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 83 if 0 alt 0 proto 2 vid 0x4348 pid 0x5584
Oct 21 10:11:37 laptop kernel: [17181339.600000] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -84
Oct 21 10:11:37 laptop kernel: [17181339.808000] usb 1-1: USB disconnect, address 83
Oct 21 10:11:37 laptop kernel: [17181339.808000] drivers/usb/class/usblp.c: usblp0: removed
Oct 21 10:11:38 laptop kernel: [17181341.560000] usb 1-1: new full speed USB device using uhci_hcd and address 84
Oct 21 10:11:39 laptop kernel: [17181341.704000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 84 if 0 alt 0 proto 2 vid 0x4348 pid 0x5584
Oct 21 10:11:39 laptop kernel: [17181342.076000] usb 1-1: USB disconnect, address 84
Oct 21 10:11:39 laptop kernel: [17181342.076000] drivers/usb/class/usblp.c: usblp0: removed

Does this give anyone any indication of what is going on ?

The laptop is running Ubuntu Dapper and this printer and cable worked perfectly on a Centos server previously.

Anyone ... ?

---

### Post by ReaderRat on 2006-10-20
What do you mean by a 
> via a usb to parallel cable.??

---

### Post by McHenry on 2006-10-21
My printer has a centronics port however my laptop only has usb ports to I have a use to centronics cable.

---

### Post by ReaderRat on 2006-10-22
Long ago, I had issues with Centronics cables, in that, if they were too long or poorly shielded (Yeah, this was a long time ago) some of the output got scrambled st times. Don't know if this is the problem here.

---

### Post by McHenry on 2006-10-23
The same cable & printer functions perfectly on a Centos server so it must either be Ubuntu or the laptop

---

