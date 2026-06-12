---
title: "ubuntu thinks my smc eth1 is VGA card"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by glenndavy on 2006-12-20
Hi
Ive got an SMC 9452tx 1GB ethernet card. I got it working  pretty quick using the docs at ldp to determine it used the ns83820 module.

It mysteriously stopped working after a reboot 1 day. While I can modprobe ns83820 with no errors, ifconfig ... up tells mel there is not such device.

 When I look at lspci, it tells me that this card is a vga card!:

02:04.0 Ethernet Controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter(rev 11)

Im hoping that this is the cause of my confusion and lspci, can be corrected somehow

Any ideas, anyone?

Thanks 
Glenn

---

