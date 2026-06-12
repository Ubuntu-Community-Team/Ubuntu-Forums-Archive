---
title: "Samsung SCX-4200 multifunction scannerproblem"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by johatte on 2006-11-07
Printer is functioning, but scanner is not. It has been a really tedious job to install this device in Ubuntu Edgy. Install scripts were not functioning, so I had to install drivers manually. 
When I try to start the scanner with xsane I get following error log:

Nov  7 08:29:22 jubuntu rmmod: ERROR: Module mfpportprobe does not exist in /proc/modules 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Module mfpport does not exist in /proc/modules 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Removing 'lp': Operation not permitted 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Module parport_pc is in use 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Module ppdev does not exist in /proc/modules 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Module parport is in use by lp,parport_pc 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Removing 'lp': Operation not permitted 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Module parport_pc is in use 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Module ppdev does not exist in /proc/modules 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Module parport is in use by lp,parport_pc 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Removing 'lp': Operation not permitted 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Module parport_pc is in use 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Module ppdev does not exist in /proc/modules 
Nov  7 08:29:22 jubuntu rmmod: ERROR: Module parport is in use by lp,parport_pc 

What does this mean? And how do I solve the problem?

Thank you in advance

---

### Post by Marcelo Fernández on 2007-02-20
Did you fix this problem? I have the same issue.... and this:

localhost kernel: [  382.031636] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -71
localhost kernel: [  382.031649] drivers/usb/class/usblp.c: usblp0: error -71 reading from printer

also appears in the syslog. :( 

Thanks,
Marcelo

---

### Post by Marcelo Fernández on 2007-02-20
I think I could solve this problem; talking to the device with USB 1.1 seems to work. Look at:

[http://www.ubuntuforums.org/showthread.php?t=245545&page=2](http://www.ubuntuforums.org/showthread.php?t=245545&page=2)

You have to:
# rmmod usblp
# rmmod ehci_hcd
# modprobe usblp

And the scanner worked for me. :guitar: 

Cheers!
Marcelo

---

