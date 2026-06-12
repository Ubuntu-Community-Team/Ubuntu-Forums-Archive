---
title: "Connecting USB Phone"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by Onesimus on 2007-07-29
Hi

I am trying to connect my mobile phone using the USB port.  However, KMobileTools is unable to recognise the phone.  Having searched on their forums it was indicated that I needed to:  *install the kernel USB ACM driver.  In 2.6 kernels it's called cdc-acm, and you can find it in Device Drivers->USB support->USB Modem (CDC-ACM)*

How would I go about doing this in Feisty ?

When I type dmesg it provides:

  [61945.120000] usb 3-1: new full speed USB device using uhci_hcd and address 2
  [61945.288000] usb 3-1: configuration #1 chosen from 1 choice

Any ideas would be greatly appreciated

---

