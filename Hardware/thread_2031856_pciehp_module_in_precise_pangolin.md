---
title: "pciehp module in precise pangolin?"
date: 2012-07-22
forum: Hardware
---

### Post by mcarro on 2012-07-22
Hi.  I am trying to load the pciehp module in precise pangolin (ubuntu 12.04) in order to try to make a sveon sct110 usb 3.0 card work.  I am using the Ubuntu  3.2.0-26-generic-pae kernel, and after loading the module (with modprobe) it does not appear listed (with lsmod).  A 'find' under /lib/modules does not show it compiled as a module.  Can I assume it is compiled as part of the kernel? 

(In any case my problem is the sveon card - I have searched and followed the instructions at help.ubuntu.com to no avail so far; any hints are welcome!)

---

### Post by mcarro on 2012-07-23
It seems that booting with the card inserted makes the kernel recognize the card: the following appears in the output of lspci 

USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)


A USB 3.0 disk can then be mounted. I am not yet sure if it is working at USB 3.0 speed.  However, if I remove the card and insert it again, it is not recognized.

---

