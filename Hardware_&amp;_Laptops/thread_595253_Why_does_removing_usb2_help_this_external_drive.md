---
title: "Why does removing usb2 help this external drive?"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by joncheyne on 2007-10-28
Hiya

After hunting around, I found that disabling USB2 with the command

modprobe -r ehci_hcd

allows my HItachi Deskstar 250 to connect to my Gutsy laptop.

(It is inside a Sumvision Aqua Media housing).

If I connect without the above command, I get loads (loads!) of these

  usb 5-5: reset high speed USB device using ehci_hcd and address 4

..and the device never shows up ... (Same in windows XP - if the drive is on, nothing shows up in storage management, push the power off and the drives appear.)

Anyway, back to ubuntu. What does this all mean and is this a problem with the enclosure or the drive? 

Cheers

Jon

---

